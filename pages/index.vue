<template>
  <div class="container-fluid">
    <main class="row">
      <div class="col-md-12">
      <searchInput/>
      </div>
      <!-- <Card :product="myproduct" /> -->
      <Card v-for="product in this.$state.products" :key="product.id" :product="product" />
    </main>
  </div>
</template>

<script>

import Card from '@/components/Card'
import searchInput from '@/components/searchInput'
export default {
  components:{
    Card,
    searchInput
  },
   asyncData(context) {
      return fetch(`https://fakestoreapi.com/products`)
      .then(res=>res.json())
      .then(rs =>{ 
        return context.$state.products = rs 
      })
   },
  data(){
    return{
      // myproduct:{
      //   id:'1',
      //   title:'T-Shirt',
      //   price:'200',
      // }
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
main {
  padding-top: 200px;
}
</style>
