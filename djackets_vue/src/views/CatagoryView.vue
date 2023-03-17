<template>
  <div class="page-catagory">
    <div class="columns is-multiline">
        <div class="column is-12">
            <h2 class="is-size-2 has-text-centered">{{ catagory.name }}</h2>
        </div>
    </div>

    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">Latest Products</h2>
      </div>

      <ProductBox v-for="product in catagory.products" :key="product.id" :product="product"/>

    </div>
  </div>
</template>

<script>
import axios from 'axios'
import {toast} from 'bulma-toast'
import ProductBox from '../components/ProductBox.vue'


export default {
    name:'Catagory',
    
    components:{
        ProductBox,
    },
    data(){
        return{
            catagory:{
                products:[]
            }
        }
    },
    methods:{
        async getCatagory(){
            const slug  = this.$route.params.catagory_slug
            const response = await axios.get(`http://localhost:8000/api/v1/products/${slug}/`)
            this.catagory=response.data  
        }
    },
    created(){
        this.getCatagory()
    },
    watch:{
        $route(to,from){
            if(to.name === 'Catagory'){
                this.getCatagory()
            }
        }

    }
    

}
</script>

<style>

</style>