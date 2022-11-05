<template>
  <div class="main">
    <div class="loginL">
      <img src="@/assets/logo2.png" class="logo" />
      <div class="text-left">
        <h1 class="mb-2">Sign in to your account</h1>
        <h5>Or <a class="linktext">start your 14-day free trial</a></h5>
      </div>
      <div style="padding-top: 2px">
        <h4>Sign in with</h4>
        <button
          class="btn secondary btnlogin"
          href="https://www.facebook.com/login.php/"
          target="_blank"
        >
          <i class="fa-brands fa-facebook"></i>
        </button>
        <button
          class="btn secondary btnlogin"
          href="https://twitter.com/login/"
          target="_blank"
        >
          <i class="fa-brands fa-twitter"></i>
        </button>
        <button
          class="btn secondary btnlogin"
          href="https://www.facebook.com/login.php/"
          target="_blank"
        >
          <i class="fa-brands fa-github"></i>
        </button>
      </div>
      <h5 class="h5-line"><span class="h5-span"> Or continue with</span></h5>
      <div>
        <div>
          <label>Email address</label>
          <input
            class="inputText"
            v-model="email"
            placeholder="Email address"
            style="width: 100%"
            type="email"
          />
        </div>
        <div>
          <label>password</label>
          <input
            class="inputText"
            v-model="password"
            placeholder="Password"
            style="width: 100%"
            type="password"
          />
        </div>
        <div class="gridlogin">
          <div class="gridloginL">
            <input
              type="checkbox"
              v-model="ChkRemember"
              class="checkbox"
              checked="checked"
              id="ChkRemember"
            />
            <label for="ChkRemember">Remember me</label>
          </div>
          <div class="gridloginR">
            <a class="linktext">Forger Password?</a>
          </div>
        </div>
        <div>
          <button class="btn primary" @click="Login" style="width: 100%">
            Login
          </button>
        </div>
      </div>
    </div>
    <div class="loginR">
      <img src="@/assets/wallpaper.jpg" class="wallpaper" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "app-login",
  data: () => ({
    email: "",
    password: "",
    ChkRemember: "",
    snackbar: false,
  }),
  methods: {
    Login() {
      // Test Login
      //  body:{
      //   email: "eve.holt@reqres.in",
      //   password: "cityslicka"
      //}
      axios
        .post("https://reqres.in/api/login", {
          email: this.email,
          password: this.password,
        })
        .then((response) => {
          console.log("success", response);
          //check remember me == true setItemlocalStorage
          if (this.ChkRemember) {
            console.log(this.ChkRemember);
            const vals = JSON.stringify({
              email: this.email,
              password: this.password,
              ChkRemember: this.ChkRemember,
            });
            localStorage.setItem("localVals", vals);
          } else {
            localStorage.removeItem("localVals");
          }
          this.$router.push({ name: "dataEmployeePage" });
        })
        .catch((err) => {
          this.snackbar = true;
          console.log("error", err);
        });
    },
  },
  mounted() {
    if (localStorage.getItem("localVals")) {
      try {
        console.log(JSON.parse(localStorage.getItem("localVals")));
        var jsonLocal = JSON.parse(localStorage.getItem("localVals"));
        this.email = jsonLocal.email;
        this.password = jsonLocal.password;
        this.ChkRemember = jsonLocal.ChkRemember;
      } catch (e) {
        localStorage.removeItem("localVals");
      }
    }
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/button.scss";

.btnlogin {
  width: 8rem;
  font-size: 1.5rem;
  padding: 6px;
}
.main {
  display: grid;
  grid-template-areas: "left right";
  gap: 5rem;
  padding: 5rem;
  margin-top: 3rem;
  margin-bottom: 3rem;
  margin-left: 10rem;
  margin-right: 10rem;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border-radius: 10px;
}
.gridlogin {
  display: grid;
  grid-template-areas: "left right";
  gap: 10px;
  padding: 10px;
}
.gridloginL {
  grid-area: left;
}
.gridloginR {
  grid-area: right;
}
.loginL {
  text-align: left;
  grid-area: left;
  float: right;
}
.loginR {
  display: block;
  grid-area: right;
  // width: 50%;
}

.wallpaper {
  float: right;
  width: 100%;
  height: 100%;
}

.btnSignin {
  width: 9rem;
  margin: 0.5rem;
  background-color: #6c757d;
}

.h5-line {
  // position: relative;
  // z-index: 1;
  // overflow: hidden;
  // text-align: center;
  width: 100%;
  text-align: center;
  border-bottom: 1px solid #000;
  line-height: 0.1em;
  margin: 10px 0 20px;
}

// .h5-line:before .h5-line:after {
//   position: absolute;
//   top: 51%;
//   overflow: hidden;
//   width: 50%;
//   height: 1px;
//   content: "\a0";
//   background-color: #000000;
// }

// .h5-line:before {
//   margin-left: -50%;
//   text-align: right;
// }
.h5-span {
  background: #fff;
  padding: 0 10px;
}
.inputText {
  width: 300px;
  height: 35px;
  margin: 0.5rem 0rem 1rem;
  border-radius: 4px;
}
.logo {
  margin-top: 2%;
  width: 6vw;
}
.checkbox {
  text-align: left;
}
</style>
