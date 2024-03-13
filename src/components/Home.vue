<template>
  <div>
    <header>
      <nav>
        <div class="container">
          <div class="logo">
            <h1>Your E-commerce</h1>
          </div>
          <ul class="menu">
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/about">About us</router-link></li>
            <li><router-link to="/products">Products</router-link></li>
            <li><router-link to="/contact">Contact us</router-link></li>
          </ul>
        </div>
      </nav>
    </header>
    
    <main>
      <section class="banner">
        <div class="container">
          <img src="" alt="Banner Image">
          <h2>Welcome to Your E-commerce Platform</h2>
        </div>
      </section>
      
      <section class="about-us">
        <div class="container">
          <h2>About Us</h2>
          <p>This is where you can introduce your e-commerce platform, talk about your mission, vision, and values, and share any other relevant information about your company.</p>
        </div>
      </section>
      
      <section class="contact-us">
        <div class="container">
          <h2>Contact Us</h2>
          <p>Contact us section content...</p>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: "HomePage",
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
