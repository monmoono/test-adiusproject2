<template>
  <div class="mainsitecolor topnav">
    <router-link to="/">
      <a link class="btn primary"> Home </a>
    </router-link>
    <router-link to="">
      <a link class="btn primary"> Solutions </a>
    </router-link>
    <router-link to="/login">
      <a link class="btn primary"> Sign in </a>
    </router-link>
  </div>

  <router-view />

  <footer>
    <div class="footer">
      <div class="grid-container">
        <div class="grid-item">
          <img src="@/assets/logo2.png" class="imgfooter" />
        </div>
        <div class="grid-item">
          <div class="footer-list">
            <h3>Products</h3>
            <ul>
              <li v-for="(item, index) in itemsFt1" :key="index" link>
                {{ item.title }}
              </li>
            </ul>
          </div>
        </div>
        <div class="grid-item">
          <h3>Company</h3>
          <ul>
            <li v-for="(item, index) in itemsFt2" :key="index" link>
              {{ item.title }}
            </li>
          </ul>
        </div>
        <div class="grid-item">
          <h3>Sign up for our newsistter</h3>
          <p class="subtext">
            The latest deals and saving, sent to your inbox weekly.
          </p>
          <ul>
            <input />
            <button class="btn primary">SUBMIT</button>
          </ul>
        </div>
      </div>
      <div class="subfooter">
        <p style="color: black">
          Copyright © 2022 by
          <a href="https://www.facebook.com/jirapatjames/" target="_blank">
            James-Jirapat</a
          >
        </p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    itemsFt1: [
      { title: "Bage" },
      { title: "Tees" },
      { title: "Object" },
      { title: "Home Goods" },
      { title: "Accessories" },
    ],
    itemsFt2: [
      { title: "Who a are" },
      { title: "Sustainability" },
      { title: "Press" },
      { title: "Careers" },
      { title: "Terms & Conditions" },
      { title: "Privacy" },
    ],
  }),

  methods: {},
};
</script>

<style lang="scss">
@import "@/assets/button.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  // color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.topnav {
  overflow: hidden;
}

.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.imgfooter {
  width: 6vw;
  padding: 0;
}

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  padding: 10px;
}
.grid-item {
  padding: 10px;
  font-size: 30px;
  text-align: center;
  margin: 0;
}

.footer {
  border-top: 5px solid #ddd;
  left: 0;
  bottom: 0;
  width: 100%;
  // background-color: #673ab7;
  color: white;
  text-align: center;
  font-size: 1rem;
}

h3 {
  margin-bottom: 4vh;
  font-size: 1.6vw;
  color: #000;
}
li {
  color: #000;
  margin-bottom: 2vh;
  font-size: 1vw;
  cursor: pointer;
  padding-bottom: 1vh;

  &:hover {
    background-color: #f4f4f4;
    border-radius: 4px;
  }
}

ul {
  display: inline-block;
}

.subtext {
  color: #000;
  font-size: 0.9rem;
  opacity: 0.9;
}

input {
  width: 300px;
  height: 25px;
  margin: 0 1.1rem;
  border-radius: 4px;
}

.subfooter {
  text-align: center;
  display: inline-block;
  background-color: #f4f4f4;
  width: 100%;
  margin-bottom: 0px;
  padding: 30px 0px;
  font-size: 15px;
  color: #aaaaaa;
}
</style>
