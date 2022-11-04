<template>
  <div class="main">
    <div class="loginL">
      <img src="@/assets/logo2.png" class="logo" />
      <div class="text-left">
        <h1 class="mb-2">Sign in to your account</h1>
        <h5>Or <a class="linktext">start your 14-day free trial</a></h5>
      </div>
      <div style="padding-top: 20px">
        <h4>Sign in with</h4>
        <button
          class="btn secondary"
          href="https://www.facebook.com/login.php/"
          target="_blank"
        >
          facebook
        </button>
        <button
          class="btn secondary"
          href="https://twitter.com/login/"
          target="_blank"
        >
          twitter
        </button>
        <button
          class="btn secondary"
          href="https://www.facebook.com/login.php/"
          target="_blank"
        >
          githun
        </button>
      </div>
      <h5 class="h5-line">Or continue with</h5>
      <div>
        <input
          v-model="email"
          placeholder="Email"
          style="width: 100%"
          type="email"
        />
        <input
          v-model="password"
          placeholder="Password"
          style="width: 100%"
          type="password"
        />
        <div class="gridlogin">
          <div>
            <input
              type="checkbox"
              v-model="ChkRemember"
              class="checkbox"
              checked="checked"
              id="ChkRemember"
            />
            <label for="ChkRemember" style="grid-area: left">Remember me</label>
          </div>
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

.main {
  display: grid;
  grid-template-areas: "left left right right";
  gap: 10px;
  padding: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  margin: 2%;
}
.gridlogin {
  display: grid;
  grid-template-areas: "left right";
  gap: 10px;
  padding: 10px;
}

.loginL {
  text-align: left;
  grid-area: left;
}
.loginR {
  grid-area: right;
}

.wallpaper {
  width: 50%;
}

.btnSignin {
  width: 9rem;
  margin: 0.5rem;
  background-color: #6c757d;
}

.h5-line {
  position: relative;
  z-index: 1;
  overflow: hidden;
  text-align: center;
}

.h5-line:before .h5-line:after {
  position: absolute;
  top: 51%;
  overflow: hidden;
  width: 50%;
  height: 1px;
  content: "\a0";
  background-color: #e0e0e0;
}

.h5-line:before {
  margin-left: -50%;
  text-align: right;
}

input {
  width: 300px;
  height: 25px;
  margin: 0 1.1rem;
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
