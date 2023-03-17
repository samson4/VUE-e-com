<template>
  <div class="page-search">
    <div class="columns is-multiline">
        <div class="column is-12">
            <h1 class="title">Search</h1>
            <h2 class="is-size-5 has-text-grey">Search terms:"{query}"</h2>
        </div>
        <ProductBox v-for="product in products" :key="product.id" :product="product" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import ProductBoxVue from '../components/ProductBox.vue'
export default {
    name:"Search",
    components:{
        ProductBoxVue
    },
    data(){
        return {
            products:[],
            query:''
        }
    },
    mounted(){

    }
}
</script>

<style>

</style>