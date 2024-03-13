<template>
  <Header/>
  <h1>Hello this is Home Page</h1>
</template>

<script>
import Header from './Header.vue';

export default {
  name: "HomePage",
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

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.container .logo {
  text-align: center;
  padding-bottom: 10px;
  padding: auto;
}

header {
  background-color: #333;
  padding: 10px 0;
  color: white;
}

.logo h1 {
  font-size: 24px;
}

.menu {
  list-style: none;
  float: right;
}

.menu li {
  display: inline-block;
  margin-left: 20px;
}

.menu li a {
  text-decoration: none;
  color: black;
}

.banner {
  text-align: center;
  padding: 50px 0;
  background-color: #f8f8f8;
}

.banner img {
  max-width: 100%;
  height: auto;
  margin-bottom: 20px;
}

.banner h2 {
  font-size: 36px;
  color: #333;
}

.about-us,
.contact-us {
  padding: 50px 0;
}

.about-us h2,
.contact-us h2 {
  text-align: center;
  margin-bottom: 30px;
}

.about-us p,
.contact-us p {
  text-align: center;
}
</style>
