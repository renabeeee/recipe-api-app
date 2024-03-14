<template>
  <div id="login">
    <div class="main">
      <div class="header-text">
        <h2 class="header-text">Login</h2>
      </div>
      <ul>
        <li v-for="error in errors" :key="error">{{ error }}</li>
      </ul>
      <form @submit.prevent="handleSubmit">
        <div class="inputEmail">
          <label for="email">Email:</label>
          <input name="email" type="email" id="email" required />
        </div>
        <div class="inputPassword">
          <label for="password">Password:</label>
          <input name="password" type="password" id="password" required />
        </div>
        <button class="submit-button" type="submit">Login</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "LoginForm",
   components: {
   },
  data() {
    return {
      errors: [],
    };
  },

  methods: {
    handleSubmit(event) {
      this.errors = [];
      const params = new FormData(event.target);
      axios
        .post("http://localhost:3000/sessions.json", params)
        .then((response) => {
          console.log(response.data);
          axios.defaults.headers.common["Authorization"] =
            "Bearer " + response.data.jwt;
          localStorage.setItem("jwt", response.data.jwt);
          event.target.reset();
          window.location.href = "/";
        })
        .catch((error) => {
          console.log(error.response);
          this.errors = ["Invalid email or password"];
        });
    },
  },
};
</script>

<style scoped>
/* Add your component-specific styles here */
</style>
