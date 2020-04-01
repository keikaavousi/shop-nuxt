<template>
  <div class="col-md-3">
    <div class="card">
      <div class="card-top">
          <img :src="product.image" class="card-img">
      </div>
      <div class="card-body">
          <h3>{{product.title}}</h3>
          <span>{{product.price}}$</span>
          <nuxt-link class="btn btn-light" :to="`/products/${product.id}`">View Details</nuxt-link>
          <button class="btn btn-info btn-block" @click="addtocart()">Add to Cart</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
      name:'Card',
      props:{
        product:{
            type:Object,
            required:true
        }
      },
       methods: {
        addtocart(){
            this.$state.cart = [...this.$state.cart,this.product]
        }
    }
  }
</script>

<style scoped>
.card-img{
  width:150px;
  display: block;
  margin:10px auto
}
.card-body h3,.card-body span,.card-body a{
    display: block;
    margin-bottom: 10px;
}
</style>