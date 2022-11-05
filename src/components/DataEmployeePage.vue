<template>
  <div class="hello">
    <div class="text-home">DataEmployeePage</div>
    <div class="com">
      <div class="box2">
        <div class="card" v-for="(item, index) in items" :key="index">
          <img :src="item.avatar" class="img" alt="Avatar" />
          <div class="container">
            <h4>
              <b class="name">{{ item.first_name + "" + item.last_name }}</b>
            </h4>
            <p class="email">{{ item.email }}</p>
            <p class="iconadmin">Admin</p>
          </div>
          <div>
            <button class="iconcard" style="float: left">
              <i class="fa-solid fa-envelope"></i>Email
            </button>
            <button class="iconcard" style="float: right; border-right: none">
              <i class="fa-solid fa-phone"></i>Phone
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  snackbar: false,
  data: () => ({
    items: [],
  }),
  created() {
    axios.get("https://reqres.in/api/users").then((resp) => {
      let lg = resp.data.data;
      var arr = [];
      for (let i = 0; i < lg.length; i++) {
        var obj = {};
        obj = {
          id: resp.data.data[i].id,
          email: resp.data.data[i].email,
          first_name: resp.data.data[i].first_name,
          last_name: resp.data.data[i].last_name,
          avatar: resp.data.data[i].avatar,
        };
        arr.push(obj);
      }
      this.snackbar = true;
      //Show data by sort the characters in a string alphabetically
      arr.sort((a, b) => {
        const nameA = a.first_name.toUpperCase();
        const nameB = b.first_name.toUpperCase();
        if (nameA < nameB) {
          return -1;
        }
        if (nameA > nameB) {
          return 1;
        }
        // names must be equal
        return 0;
      });
      this.items = arr;
      console.log(arr);
    });
  },
  methods: {
    snackbar() {
      this.snackbar = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 100%;
  margin: 1rem;
  padding-top: 1rem;
  text-align: center;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.container {
  padding: 2px 16px;
}

.text-home {
  font-size: 5rem;
  font-weight: bolder;
  margin-top: 1.8rem;
  text-align: center;
}
.box1 {
  grid-area: "Box1";
}

.box2 {
  display: grid;
  grid-area: "Box2";
  grid-template-columns: auto auto auto auto;
  column-gap: 2rem;
  //margin: 2rem;
}

.com {
  display: grid;
  grid-template-areas: "Box2 Box2 Box2 Box2";
  // gap: 1rem;
  margin-top: 4.5rem;
  margin-left: 4.5rem;
  margin-right: 4.5rem;
  margin-bottom: 4rem;
}

.textp {
  line-height: 1.5;
  padding-top: 1.5rem;
  font-size: 1.5rem;
  text-align: left;
  padding-left: 2rem;
}

.text-h {
  font-size: 3.5rem;
  padding-left: 2rem;
  text-align: left;
}

.img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}
.name {
  font-size: 1.5rem;
  padding-top: 1rem;
  font-weight: bold;
  padding-left: 1rem;
}

.email {
  font-size: 1.2rem;
  padding-left: 1rem;
}

.iconadmin {
  border: none;
  padding: 0.8rem 0.8rem;
  text-align: center;
  font-size: 0.9rem;
  border-radius: 0.8rem;
  color: green;
  background-color: rgb(154, 255, 154);
  margin-left: 35%;
  margin-right: 35%;
  font-weight: bold;
}

.iconcard {
  width: 50%;
  // font-size: 1.5rem;
  background-color: white;
  border-left: none;
  border-bottom: none;
  border-color: #ddd;
  color: rgb(146, 146, 146);

  .fa-solid {
    font-size: 1.5rem;
    margin: 0.4rem;
  }
  &:hover {
    background-color: #ddd;
  }
}
</style>
