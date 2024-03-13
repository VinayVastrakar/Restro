<template>
  <Header/>
  <h1>Hello this is Update Restaurent Page</h1>
</template>

<script>
import Header from './Header.vue';

export default {
  name: "UpdateRes",
  components:{
    Header
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>