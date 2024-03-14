<template>
  <div id="app">
    <img alt="Cookable logo" src="https://cookable-api.s3.us-west-1.amazonaws.com/Cookable.svg" style="width: 200px;">
    <SignupForm/>
    <LoginForm/>
  </div>
</template>

<script>
import LoginForm from './components/LoginForm.vue'
import SignupForm from './components/SignupForm.vue'

export default {
  name: 'App',
  components: {
    LoginForm,
    SignupForm,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
