<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
      <div class="hero-body has-text-centered">
        <p class="title mb6">
          Welcome to Djacket
        </p>
        <p class="subtitle">
          The best jacket store online
        </p>
      </div>
    </section>

    <ProductBox v-for="product in latestProducts" :key="product.id" :product="product"/>

  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import ProductBox from '../components/ProductBox.vue'
export default {
  
  name: 'HomeView',
  components: {
    ProductBox,
    
  },
  data(){
    return{
      latestProducts:[]
    }
  },
  mounted(){
    this.getLatestProducts()

  },
  methods:{
     async getLatestProducts(){
      this.$store.commit("setIsLoading",true)
      const response = await axios.get("http://localhost:8000/api/v1/latest-products/")
      this.latestProducts = response.data
     
      this.$store.commit("setIsLoading",false)
      
    }
  }
}
</script>

<style scoped>

</style>
