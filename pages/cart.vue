<template>
  <div class="container-fluid">
      <table class="table table-striped margin-top-md">
          <tr v-for="cart in carts" :key="cart.id">
            <td>{{cart.id}}</td>
            <td><img :src="cart.image"></td>
            <td>{{cart.title}}</td>
            <td>{{cart.price}}</td>
          </tr>
      </table>
      <h3>Total:{{total}}</h3>
  </div>
</template>

<script>

import Card from '@/components/Card'

export default {
  components:{
    Card
  },
  data(){
    return{
      myproduct:{
        id:'1',
        title:'T-Shirt',
        price:'200',
      },
      carts:this.$state.cart
    }
  },
  computed: {
      total(){
          return this.$state.cart.reduce((prev,cur)=>{
              return prev+Number(cur.price)
          },0)
      }
  },
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
.margin-top-md{
  margin-top: 100px;
}
table img{
  width:100px;
}
</style>
