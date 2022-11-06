<template>
  <div class="main">
    <div class="loginL">
      <img src="@/assets/logo2.png" class="logo" />
      <div class="text-left">
        <h1 class="mb-2 signin-h1">Sign in to your account</h1>
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
        <div style="text-align: start; font-weight: bold">
          <label>Email address</label>
          <input
            class="inputText"
            v-model="email"
            placeholder="Email address"
            style="width: 100%"
            type="email"
          />
        </div>
        <div style="text-align: start; font-weight: bold">
          <label>Password</label>
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
          <button class="btn primary" @click="Login" style="width: 100%;font-size:20px">
            Login
          </button>
        </div>
      </div>
    </div>
    <div class="loginR">
      <img src="@/assets/wallpaper.jpg" class="wallpaper" />
    </div>
  </div>
  <!-- popup alert -->
  <div id="snackbar">
    <i class="fa-solid fa-xmark"></i
    ><a style="margin-left: 20px">Wrong Email or Password !</a>
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
          console.log("error2", err);
          var x = document.getElementById("snackbar");
          // Add the "show" class to DIV
          x.className = "show";
          // After 3 seconds, remove the show class from DIV
          setTimeout(function () {
            x.className = x.className.replace("show", "");
          }, 3000);
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

.logo {
  width: 100px;
  margin-left: 1.5rem;
  margin-right: 1.5rem;
}

.main {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 97%;
  height: 100%;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border-radius: 10px;
  margin-top: 3rem;
  margin-bottom: 3rem;
  margin-left: 2rem;
  margin-right: 10%;
}

.loginL {
  width: 50%;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  display: inline-block;
  text-align: center;
  line-height: 2;
}
.loginR {
  width: 50%;
  // height: 50%;
}

.wallpaper {
  width: 100%;
  height: 100vh;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
}
.btnlogin {
  width: 8rem;
  font-size: 1.5rem;
  padding: 6px;
}

.h5-line {
  width: 100%;
  text-align: center;
  border-bottom: 1px solid #000;
  line-height: 0.1em;
  margin: 10px 0 20px;
}

.h5-span {
  background: #fff;
}
.inputText {
  width: 300px;
  height: 40px;
  border-radius: 10px;
}

.gridlogin {
  display: grid;
  grid-template-areas: "left right";
  gap: 10px;
  padding: 10px;
  font-size: 1rem;
}
.gridloginL {
  grid-area: left;
  text-align: start;
}
.gridloginR {
  grid-area: right;
  text-align: end;
}

//Snackbar https://codepen.io/pratikjain/pen/xWEERw
#snackbar {
  visibility: hidden; /* Hidden by default. Visible on click */
  min-width: 250px; /* Set a default minimum width */
  margin-left: -125px; /* Divide value of min-width by 2 */
  background-color: rgb(245, 50, 50); /* Black background color */
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

@media (max-width: 912px) {
  .loginL {
    padding-top: 1rem;
    padding-bottom: 1rem;
  }
  .loginR {
    display: none;
  }

  .btnlogin {
    width: 6rem;
  }
}

@media (max-width: 768px) {
  .btnlogin {
    width: 4rem;
  }

  .signin-h1 {
    font-size: 1.3rem;
  }

  .main {
    width: 90%;
  }
}

@media (max-width: 504px) {
  .btnlogin {
    width: 2.5rem;
  }

  .main {
    width: 80%;
  }

  .loginL {
    padding: 2rem 0 2rem 0;
    width: 80%;
  }
}
</style>
