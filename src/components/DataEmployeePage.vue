<template>
  <div class="hello">
    <div class="text-home">DataEmployeePage</div>
    <div class="com">
      <div class="box2" v-for="(item, index) in items" :key="index">
        <div class="card">
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
    <!-- popup alert -->
    <div id="snackbar">
      <i class="fa-solid fa-check"></i
      ><a style="margin-left: 20px">Successful login</a>
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
      var x = document.getElementById("snackbar");
      // Add the "show" class to DIV
      x.className = "show";
      // After 3 seconds, remove the show class from DIV
      setTimeout(function () {
        x.className = x.className.replace("show", "");
      }, 3000);
      console.log(arr);
    });
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
  grid-template-columns: auto;
  // column-gap: 2rem;
  //margin: 2rem;
}

.com {
  display: grid;
  grid-template-areas: "Box2 Box2 Box2 Box2";
  // gap: 1rem;
  column-gap: 4.5rem;
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

//Snackbar https://codepen.io/pratikjain/pen/xWEERw
#snackbar {
  visibility: hidden; /* Hidden by default. Visible on click */
  min-width: 200px; /* Set a default minimum width */
  margin-left: -125px; /* Divide value of min-width by 2 */
  background-color: rgb(65, 187, 49); /* Black background color */
  color: #fff; /* White text color */
  text-align: center; /* Centered text */
  border-radius: 2px; /* Rounded borders */
  padding: 16px; /* Padding */
  position: fixed; /* Sit on top of the screen */
  z-index: 1; /* Add a z-index if needed */
  left: 50%; /* Center the snackbar */
  top: 30px; /* 30px from the bottom */
  border-radius: 10px;
}

/* Show the snackbar when clicking on a button (class added with JavaScript) */
.show {
  visibility: visible !important; /* Show the snackbar */

  /* Add animation: Take 0.5 seconds to fade in and out the snackbar.
However, delay the fade out process for 2.5 seconds */
  -webkit-animation: fadein 0.5s, fadeout 0.5s 2.5s;
  animation: fadein 0.5s, fadeout 0.5s 2.5s;
}

/* Animations to fade the snackbar in and out */
@-webkit-keyframes fadein {
  from {
    top: 0;
    opacity: 0;
  }
  to {
    top: 30px;
    opacity: 1;
  }
}

@keyframes fadein {
  from {
    top: 0;
    opacity: 0;
  }
  to {
    top: 30px;
    opacity: 1;
  }
}

@-webkit-keyframes fadeout {
  from {
    top: 30px;
    opacity: 1;
  }
  to {
    top: 0;
    opacity: 0;
  }
}

@keyframes fadeout {
  from {
    top: 30px;
    opacity: 1;
  }
  to {
    top: 0;
    opacity: 0;
  }
}
</style>
