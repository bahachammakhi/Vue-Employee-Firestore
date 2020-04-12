<template>
  <div class="container">
    <div
      class="z-depth-1 grey lighten-4 row card-panel"
      style="display: inline-block; padding: 32px 48px 0px 48px; border: 1px solid #EEE;"
    >
      <h5>Login</h5>
      <form class="col s12" method="post">
        <div class="row">
          <div class="col s12"></div>
        </div>

        <div class="row">
          <div class="input-field col s12">
            <input v-model="email" class="validate" type="email" name="email" id="email" />
            <label for="email">Enter your email</label>
          </div>
        </div>

        <div class="row">
          <div class="input-field col s12">
            <input
              v-model="password"
              class="validate"
              type="password"
              name="password"
              id="password"
            />
            <label for="password">Enter your password</label>
          </div>
          <label style="float: right;">
            <a class="pink-text" href="#!">
              <b>Forgot Password?</b>
            </a>
          </label>
        </div>

        <br />
        <center>
          <div class="row">
            <button
              v-on:click="login"
              type="submit"
              name="btn_login"
              class="col s12 btn btn-large waves-effect indigo"
            >Login</button>
          </div>
        </center>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: "login",
  data: function() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    login: function(e) {
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            console.log("user", user);
            alert(`You are logged in as  ${user.user.email}`);
            this.$router.go({
              path: this.$router.path
            });
          },
          err => {
            alert(err.message);
          }
        );
      e.preventDefault();
    }
  }
};
</script>