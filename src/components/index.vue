<template>
  <div class="hello">
    <div class="text-home">Welcom to website</div>
    <div class="com">
      <div class="box1">
        <h1 class="text-h">Meet our leadership</h1>
        <div class="textp">
          <p>
            Libero fames augue nisl porttitor nisi,quis. Id ac elit odio vitae
          </p>
          <p>elementum enim vitae ullamcorper suspendisse.Vivamus fringilla.</p>
        </div>
      </div>
      <div class="box2">
        <table v-for="(item, index) in items" :key="index">
          <tr>
            <td><img :src="item.avatar" class="img" /></td>
            <div class="name">
              <td>{{ item.first_name + "" + item.last_name }}</td>
            </div>
            <div class="email">
              <td>{{ item.email }}</td>
            </div>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
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
      this.items = arr;
      console.log(arr);
      const btn = document.getElementById("login");
      btn.style.backgroundColor = "green";
      btn.textContent = "Sign in";
    });
  },
};
</script>

<style lang="scss" scoped>
.hello {
  font-family: "Dosis", sans-serif;
}
.text-home {
  font-size: 5rem;
  font-weight: bolder;
  margin-top: 1.8rem;
  text-align: center;
}
.box1 {
  grid-area: "Box1";
  margin-left: 4rem;
}

.box2 {
  display: grid;
  grid-area: "Box2";
  grid-template-columns: auto auto;
  // margin: 2rem;
}

.com {
  display: grid;
  grid-template-areas: "Box1 Box2 Box2";
  // gap: 1rem;
  margin-top: 4.5rem;
  margin-bottom: 5rem;
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
  padding-top: 1rem;
}
@media (max-width: 912px) {
  .box2 {
    grid-template-columns: auto;
  }
  .text-home {
    font-size: 2.5rem;
  }

  .text-h {
    font-size: 1.5rem;
    // padding-left: 1rem;

    text-align: center;
  }
  .textp {
    // line-height: 1;

    font-size: 1rem;
  }

  .img {
    width: 70px;
    height: 70px;
  }
  .name {
    font-size: 1.2rem;
  }
  .email {
    font-size: 1rem;
  }

  .box1 {
    margin-left: 1rem;
    padding-left: 0.5rem;
  }
}
@media (max-width: 468px) {
  .com {
    display: block;
    margin-top: 2rem;
    margin-bottom: 1.5rem;
  }
  .textp {
    display: none;
  }

  .text-h {
    padding-left: 0rem;
    padding-bottom: 1.5rem;
  }

  .text-home {
    font-size: 2rem;
  }

  .box2 {
    margin-left: 2rem;
  }
}
</style>
