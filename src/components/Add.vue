<template>
  <Header />
  <h1>Hello this is Add Restaurent Page</h1>
  <form class="add">
    <input
      type="text"
      placeholder="Enter Name"
      v-model="restaurant.name"
      name="name"
    />
    <input
      type="text"
      placeholder="Address"
      v-model="restaurant.address"
      name="address"
    />
    <input
      type="text"
      placeholder="Contact"
      v-model="restaurant.contact"
      name="contact"
    />
    <button type="button" v-on:click="addRestaurant">Add New Restaurant</button>
  </form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';

export default {
  name: "AddRes",
  components:{
    Header
  },
  data(){
    return{
      restaurant:{
        name:'',
        address:'',
        contact:''
      }
    }
  },
  methods:{
    async addRestaurant(){
      console.warn(this.restaurant);
      const result = await axios.post("http://localhost:3000/restaurant",{
        name:this.restaurant.name,
        address:this.restaurant.address,
        contact:this.restaurant.contact
      });
      if(result.status==201){
        this.$router.push({ name: "Home" });
      }
      console.warn("result",result);
    }
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
