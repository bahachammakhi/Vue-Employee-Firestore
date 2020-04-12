<template>
  <div class="container">
    <div
      class="z-depth-1 grey lighten-4 row card-panel login"
      style="display: inline-block; padding: 32px 48px 0px 48px; border: 1px solid #EEE;"
    >
      <h3>Register</h3>
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
              class="validate"
              v-model="password"
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
              v-on:click="register"
              name="btn_login"
              class="col s12 btn btn-large waves-effect indigo"
            >Register</button>
          </div>
        </center>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: "register",
  data: function() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    register: function(e) {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            alert(`Account Created for ${user.email}`);
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

