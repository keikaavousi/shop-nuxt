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
          <tr v-for="cart in this.$state.cart" :key="cart.id">
            <tablecell :txt="cart.id"/>
            <tablecell :url="cart.image"/>
            <tablecell :txt="cart.title"/>
            <tablecell :txt="cart.price"/>
            <tablecell><inp :quantity="cart.quantity" :id="cart.id"/></tablecell>
            <tablecell><cancel @removeitem="handleRemove(cart.id)" /></tablecell>
          </tr>
      </table>
      <h3>Total:{{total.toFixed(2)}}$</h3>
      <button @click="removeAll">Remove All</button>
  </div>
</template>

<script>
import tablecell from '../components/tablecell'
import inp from '../components/inp'
import cancel from '../components/cancel'

export default {
  data(){
    return{
      carts:this.$state.cart
    }
  },
  components:{
    tablecell,
    inp,
    cancel
  },
  props:['removeitem'],
  computed: {
      total(){
          return this.$state.cart.reduce((prev,cur)=>{
              return prev+Number(cur.price*cur.quantity)
          },0)
      }
  },
  mounted(){
      if(this.$state.cart.length==0 && localStorage.getItem('cart')!=null){
          this.$state.cart = JSON.parse(localStorage.getItem('cart'))
      }
  },
  methods: {
    handleRemove(id){
        this.$state.cart = this.$state.cart.filter(n=> n.id !=id)
        localStorage.setItem('cart',this.$state.cart)
    },
    removeAll(){
      this.$state.cart = []
      localStorage.setItem('cart',this.$state.cart)
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
