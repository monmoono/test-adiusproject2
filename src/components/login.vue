<template>
  <div>
    <div>
      <div>
        <div class="text-left">
          <h1 class="mb-2">Sign in to your account</h1>
          <h5>Or <a>start your 14-day free trial</a></h5>
        </div>
        <div style="padding-top: 20px">
          <h4>Sign in with</h4>
          <button
            class="btnSignin"
            href="https://www.facebook.com/login.php/"
            target="_blank"
          ></button>
          <button
            class="btnSignin"
            href="https://twitter.com/login/"
            target="_blank"
          ></button>
          <button
            class="btnSignin"
            href="https://www.facebook.com/login.php/"
            target="_blank"
          ></button>
        </div>
        <h5 class="h5-line">Or continue with</h5>
        <div>
          <input v-model="email" placeholder="Email" type="email"/>
          <input v-model="password" placeholder="Password" type="password" />
          <div>
            <button class="btn primary" @click="Login">Login</button>
          </div>
        </div>
      </div>
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
//@import './src/assets/button.sass'
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
</style>
