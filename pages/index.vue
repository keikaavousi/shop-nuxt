<template>
  <div class="container-fluid">
    <main class="row">
      <!-- <Card :product="myproduct" /> -->
      <Card v-for="product in products" :key="product.id" :product="product"/>
    </main>
  </div>
</template>

<script>

import Card from '@/components/Card'

export default {
  components:{
    Card
  },
  asyncData(context) {
      return fetch(`https://fakestoreapi.com/products`)
      .then(res=>res.json())
      .then(rs => {
        return{
          products:rs
        }
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
main{
  padding-top:200px
}
</style>
