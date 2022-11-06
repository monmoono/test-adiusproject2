<template>

    <div class="nav mainsitecolor ">
    <router-link to="/">
      <a link class="btn primary button button-h"> Home </a>
    </router-link>
    <router-link to="" class="dropdown button ">
      <a link class="btn primary button-h">
        Solutions
        <i
          class="fa-solid fa-caret-down"
          style="font-size: 15px; color: white"
        ></i>
      </a>
      <div class="dropdown-content">
        <div class="grid-container2">
          <a
            >
            <i class="fa-solid fa-chart-simple i"></i>
            <span class="span-h">Analytics</span>
            
              <p class="span-p1">Get a better understanding of where <p>your traffic is coming from.</p></p>
            </a
          >
          <a
            ><i class="fa-solid fa-shield-halved i"></i>
            <span class="span-h">Securlity</span>
            <p class="span-p2">Your customers data will be safe and <p>secure.</p></p></a
          >
          <a
            ><i class="fa-solid fa-repeat i"></i>
            <span class="span-h">Automations</span>
            <p class="span-p3">
              Build strategic funnels that will drive <p>your customers to convert.</p>
            </p></a
          >
          <a
            ><i class="fa-solid fa-arrow-pointer i"></i>
            <span class="span-h">Engagement</span>
            <p class="span-p4">Speak directly to your customers in <p>a more meaningful way.</p></p></a
          >
          <a
            ><i class="fa-solid fa-border-all i"></i>
            <span class="span-h">Integrations</span>
            <p class="span-p5">Connect with third-party tools that <p>you're already using.</p></p></a
          >
          <a
            ><i class="fa-solid fa-file-contract i"></i>
            <span class="span-h">Report</span>
            <p class="span-p6">
              Get detailed reports that will help <p>you make more inforned
              decisions</p>
            </p></a
          >
        </div>
        <div class="grid-container3 dropdown-content2">
          <a>
            <span class="span-h-b">Emterprise</span>
            <button class="newicon" disabled>NEW</button>
            <p>Emterprise your entire team with even more advanced tools.</p></a
          >
        </div>
      </div>
    </router-link>
    <router-link to="/login">
      <a link class="btn success button-login" id="login"> Sign in </a>
    </router-link>
  </div>

  <router-view />

  <footer>
    <div class="footer">
      <div class="grid-container">
        <div class="grid-logo">
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
        <div class="grid-item1">
          <ul>
            <h3>Company</h3>
            <li v-for="(item, index) in itemsFt2" :key="index" link>
              {{ item.title }}
            </li>
          </ul>
        </div>
        <div class="grid-item2">
          <ul>
            <h3>Customer Service</h3>
            <li v-for="(item, index) in itemsFt3" :key="index" link>
              {{ item.title }}
            </li>
          </ul>
        </div>
        <div class="grid-item3 last-item">
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

<style lang="scss" scoped>
@import "@/assets/button.scss";

.nav { 
  padding: 20px ;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding-left: 0.5rem;
  padding-right: 0.5rem; 
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
}

.button {
  margin-right: auto;
  padding-left: 1rem;
  // font-weight: 700;  
}

.button-login {
  // display: inline-block;
  font-weight: 700;
  font-size: 1.25rem;

}

.button-h {
  font-size: 1.25rem;
  font-weight: 700;
}

.span-h {
  font-size: 1.1rem;
  font-weight: 900;
  padding-left: 0.4rem;
 
}

.span-p1 , .span-p5 , .span-p6 {
  padding-left: 1.89rem;
}

.span-p2 , .span-p3 {
  padding-left: 2.2rem;
}

.span-p4 {
  padding-left: 1.62rem;
}


.span-h-b {
  font-size: 1.2rem;
  font-weight: bolder;
}
// .i {
//  font-size: 3rem;
// }

// .topnav a {
//   float: left;
//   color: #f2f2f2;
//   text-align: center;
//   padding: 14px 16px;
//   text-decoration: none;
//   font-size: 17px;
// }

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

@media (max-width: 1305px) {
//   .last-item {
//    display: none;  
// }
.grid-container {
  display: grid;
  grid-template-columns:auto auto auto;
  grid-template-areas:
    'header header header'
    'main1 main2 main3'
    'footer footer footer';
  padding: 10px;
}
ul{
  text-align: left;
}
.grid-logo{
  margin: 1rem 0 1rem;
  grid-area: header;
}
.grid-item{
  grid-area: main1;
}
.grid-item1{
  grid-area: main2;
}
.grid-item2{
  grid-area: main3;
}
.grid-item3{
  grid-area: footer;
}
}

@media (max-width: 768px) {
.button-login {
  font-size: 1rem;
}
.button-h {
  font-size: 1rem;
}


}

@media (max-width: 465px) {
  i {
  font-size: 15px;
  color: blue;
}

.span-p1 , .span-p5 , .span-p6,.span-p2 , .span-p3 , .span-p4 {
  display: none;
}
.span-h {
  font-size: 0.8rem;
  font-weight: 900;
  padding-left: 0.2rem; 
}

.span-h-b {
  font-size: 1rem;
}

.newicon {
  margin: 7px;
}

ul{
  text-align: center;
}


}


</style>
