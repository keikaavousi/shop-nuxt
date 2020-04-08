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
            
            let finded = this.$state.cart.find(n=>{
              return n.id == this.product.id
            })

            if(!finded){
             this.$state.cart = [...this.$state.cart,{id:this.product.id,title:this.product.title,image:this.product.image,price:this.product.price,quantity:1}]
            localStorage.setItem('cart',JSON.stringify(this.$state.cart))
            }




            console.log(this.$state.cart)


            //this.$state.cart = [...this.$state.cart,this.product]
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