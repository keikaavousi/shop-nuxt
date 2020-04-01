<template>
<div class="container">
  <main class="row">
      <div class="col-md-6">
        <img :src="product.image" class="img-responsive"/>
      </div>
      <div class="col-md-6 text-left">
           <h1>{{product.title}}</h1>
           <h3>{{product.price}}$</h3>
           <button class="btn btn-dark" @click="addtocart">Add to cart</button>

          <p class="margin-top-lg">{{product.description}}</p>
          <nuxt-link to="">{{product.category}}</nuxt-link>
      </div>
   </main>
</div>
</template>

<script>
export default {
    asyncData(context) {
        return fetch(`https://fakestoreapi.herokuapp.com/products/${context.params.id}`)
        .then(res=>res.json())
        .then(product=>{
            return{
                product
            }
        })
    },
    methods: {
        addtocart(){
            this.$state.cart = [...this.$state.cart,this.product]
        }
    },
}
</script>

<style>
.img-responsive{
    width:300px;
    max-width:100%
}
.margin-top-lg{
    margin-top:70px
}
.text-left{
    text-align:left
}
</style>