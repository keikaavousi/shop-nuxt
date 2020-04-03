<template>
  <div class="container-fluid">
      <table class="table table-striped margin-top-md">
        <thead>
          <tr>
              <th>Id</th>
              <th>img</th>
              <th>title</th>
              <th>price</th>
              <th>quantity</th>
            </tr>
        </thead>
          <tr v-for="cart in carts" :key="cart.id">
            <tablecell :txt="cart.id"/>
            <tablecell :txt="cart.image"/>
            <tablecell :txt="cart.title"/>
            <tablecell :txt="cart.price"/>
            <tablecell><inp :quantity="cart.quantity" :id="cart.id"/></tablecell>
            <!-- <td>{{cart.id}}</td>
            <td><img :src="cart.image"></td>
            <td>{{cart.title}}</td>
            <td>{{cart.price}}</td>
            <td><input min="1" type="number" @change="handleNum(cart.id)" :value="cart.quantity"></td> -->
          </tr>
      </table>
      <h3>Total:{{total}}</h3>
  </div>
</template>

<script>
import tablecell from '../components/tablecell'
import inp from '../components/inp'

export default {
  data(){
    return{
      carts:this.$state.cart
    }
  },
  components:{
    tablecell,
    inp
  },
  computed: {
      total(){
          return this.$state.cart.reduce((prev,cur)=>{
              return prev+Number(cur.price)
          },0)
      }
  },
  methods: {
    handleNum(id){
        console.log(id)
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
