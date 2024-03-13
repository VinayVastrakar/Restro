<template>
  <Header />
  <h1>Hello {{ name }} Welcom on Home Page</h1>
  <table border="1">
    <tr>
      <!-- <td>Id</td> -->
      <td>Name</td>
      <td>Address</td>
      <td>Contact</td>
      <td>Actions</td>
    </tr>
    <tr v-for="item in restaurants" :key="item.id">
      <!-- <td>{{item.id}}</td> -->
      <td>{{ item.name }}</td>
      <td>{{ item.address }}</td>
      <td>{{ item.contact }}</td>
      <td>
        <router-link :to="'/update/' + item.id">Update</router-link>
        <button v-on:click="deleterRestaurant(item.id)">Delete</button>
      </td>
    </tr>
  </table>

  <div class="product-container">
    <img
      src="https://c.static-nike.com/a/images/f_auto/dpr_3.0,cs_srgb/h_500,c_limit/g1ljiszo4qhthfpluzbt/123-joyride-cdp-apla-xa-xp.jpg"
      alt="Product Image"
      class="product-image"
    />
    <div class="product-details">
      <h1 class="product-name">Product Name</h1>
      <p class="product-price">$99.99</p>
      <p class="product-description">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam aliquam
        est eu nisi posuere, vel sollicitudin orci feugiat. Integer dapibus
        volutpat nulla, ac congue felis suscipit sed.
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue";

export default {
  name: "HomePage",
  data() {
    return {
      name: "",
      restaurants: [],
    };
  },
  components: {
    Header,
  },
  methods: {
    async deleterRestaurant(id) {
      let result = await axios.delete("http://localhost:3000/restaurant/" + id);
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: "SignUp" });
      }
      let result = await axios.get("http://localhost:3000/restaurant");
      console.warn(result);
      this.restaurants = result.data;
    },
  },
  mounted() {
    this.loadData();
  },
};
</script>
<style>
td {
  width: 160px;
  height: 40px;
}

.product-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 50px auto;
  width: 80%;
}

.product-image {
  max-width: 200px;
  margin-right: 20px;
}

.product-details {
  max-width: 50%;
}

.product-name {
  font-size: 24px;
  margin-bottom: 10px;
}

.product-price {
  font-size: 20px;
  margin-bottom: 10px;
  color: #333;
}

.product-description {
  font-size: 16px;
  line-height: 1.5;
}
</style>
