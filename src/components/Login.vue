<template>
  <img class="logo" src="../assets/logo.png" alt="" />
  <h1>Login</h1>
  <div class="login">
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button>Login</button>
    <p>
      <router-link to="/sign-up">SignUp</router-link>
    </p>
  </div>
</template>
<script>
export default {
  name: "LogIn",
};
</script>
