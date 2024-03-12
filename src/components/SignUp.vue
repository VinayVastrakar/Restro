<template>
  <img class="logo" src="../assets/logo.png" alt="" />
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" v-model="name" placeholder="Enter Name" />
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="signUp">Sign Up</button>
  </div>
</template>
<script>
import axios from "axios"
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      console.warn("signUp", this.name, this.email, this.password);
      let result = await axios.post("http://localhost:3000/user", {
        email: this.email,
        name: this.name,
        password: this.password,
      });
      console.warn(result);
      if(result.status === 201) {
        
        localStorage.setItem("user-info", JSON.stringify(result.data));
        this.$router.push({name:'Home'})

      }
    }
  }
}
</script>
<style>
.logo {
  width: 100px;
}
.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  border: 1px solid skyblue;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  color: #fff;
  background-color: skyblue;
  cursor: pointer;
}
</style>
