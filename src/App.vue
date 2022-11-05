<template>
  <div class="mainsitecolor topnav">
    <router-link to="/">
      <a link class="btn primary"> Home </a>
    </router-link>
    <router-link to="" class="dropdown">
      <a link class="btn primary">
        Solutions
        <i
          class="fa-solid fa-caret-down"
          style="font-size: 15px; color: white"
        ></i>
      </a>
      <div class="dropdown-content">
        <div class="grid-container2">
          <a
            ><i class="fa-solid fa-chart-simple"></i>
            <h4>Analytics</h4>
            <p>
              Get a better understanding of where your traffic is coming from.
            </p></a
          >
          <a
            ><i class="fa-solid fa-shield-halved"></i>
            <h4>Securlity</h4>
            <p>Your customers data will be safe and secure.</p></a
          >
          <a
            ><i class="fa-solid fa-repeat"></i>
            <h4>Automations</h4>
            <p>
              Build strategic funnels that will drive your customers to convert.
            </p></a
          >
          <a
            ><i class="fa-solid fa-arrow-pointer"></i>
            <h4>Engagement</h4>
            <p>Speak directly to your customers in a more meaningful way.</p></a
          >
          <a
            ><i class="fa-solid fa-border-all"></i>
            <h4>Integrations</h4>
            <p>Connect with third-party tools that you're already using.</p></a
          >
          <a
            ><i class="fa-solid fa-file-contract"></i>
            <h4>Report</h4>
            <p>
              Get detailed reports that will help you make more inforned
              decisions
            </p></a
          >
        </div>
        <div class="grid-container3 dropdown-content2">
          <a>
            <h4>Emterprise</h4>
            <button class="newicon" disabled>NEW</button>
            <p>Emterprise your entire team with even more advanced tools.</p></a
          >
        </div>
      </div>
    </router-link>
    <router-link to="/login">
      <a link class="btn success"> Sign in </a>
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
            <ul>
              <h3>Products</h3>
              <li v-for="(item, index) in itemsFt1" :key="index" link>
                {{ item.title }}
              </li>
            </ul>
          </div>
        </div>
        <div class="grid-item">
          <ul>
            <h3>Company</h3>
            <li v-for="(item, index) in itemsFt2" :key="index" link>
              {{ item.title }}
            </li>
          </ul>
        </div>
        <div class="grid-item">
          <ul>
            <h3>Customer Service</h3>
            <li v-for="(item, index) in itemsFt3" :key="index" link>
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
    itemsFt3: [
      { title: "Contact" },
      { title: "Shipping" },
      { title: "Returns" },
      { title: "Warranty" },
      { title: "Secure Payments" },
      { title: "FAQ" },
      { title: "Find a store" },
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

.newicon {
  background-color: blue;
  color: white;
  border-radius: 4px;
  margin: 16px;
}

.dropbtn {
  background-color: #04aa6d;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
}

.dropdown {
  // position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 2;
  border-radius: 8px;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  text-align: left;
}

.dropdown-content a:hover {
  background-color: #ddd;
}
.dropdown-content2 a:hover {
  background-color: #f1f1f1;
  margin: 10px;
}

.dropdown:hover .dropdown-content {
  display: block;
}

.imgfooter {
  width: 6vw;
  padding: 0;
}

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto auto;
  padding: 10px;
}
.grid-container2 {
  display: grid;
  grid-template-columns: auto auto;
  padding: 10px;
}
.grid-container3 {
  display: grid;
  grid-template-columns: auto;
  background-color: #d9d9d9;
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
  color: rgb(119, 119, 119);
  margin-bottom: 2vh;
  font-size: 1vw;
  cursor: pointer;
  padding-bottom: 1vh;
  list-style-type: none;

  &:hover {
    background-color: #f4f4f4;
    border-radius: 5px;
  }
}

ul {
  margin: 0;
  padding: 0;
  display: inline-block;
  text-align: left;
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

i {
  font-size: 30px;
  color: blue;
}
</style>
