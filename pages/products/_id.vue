<template>
<div class="container">
  <main class="row">
      <div class="col-md-6">
        <img :src="product.image" class="img-responsive" @mousemove="getPos" @mouseenter="modalShow"/>
      </div>
      <div class="col-md-6 text-left">
           <h1>{{product.title}}</h1>
           <h3>{{product.price}}$</h3>
           <button class="btn btn-dark" @click="addtocart">Add to cart</button>

          <p class="margin-top-lg">{{product.description}}</p>
          <nuxt-link to="">{{product.category}}</nuxt-link>
      
      </div>
      <div class="img-modal" ref="modal">
          <!-- <div class="inner" ref="inner"></div> -->
          <img ref="inner">
      </div>
   </main>
   <!-- <no-ssr> -->
        <notifications group="cart"/>
   <!-- </no-ssr> -->
</div>
</template>

<script>
export default {
    asyncData(context) {
        return fetch(`https://fakestoreapi.com/products/${context.params.id}`)
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
            this.$notify({
                'group':'cart',
                'title':'Message',
                'text':'Successfully Added to cart!',
                'classes':['myalert']
            })
            localStorage.setItem('cart',JSON.stringify(this.$state.cart))
        },
        modalShow(){
            this.$refs.modal.style.display = "block"
           this.$refs.inner.src = this.product.image
        },
        getPos(e){
           this.$refs.inner.style.transform=`translate(${-e.clientX}px,${-e.clientY}px)`
        }
    },
}
</script>

<style scoped>
.img-responsive{
    width:300px;
    max-width:100%;
    cursor:zoom-in;
}
.margin-top-lg{
    margin-top:70px
}
.text-left{
    text-align:left
}
.img-modal{
    width:50%;
    height: 600px;
    position: absolute;
    left:70%;
    top:50%;
    transform: translate(-50%,-50%);
    border:1px solid rgba(123,123,123,0.3);
    background-color: #fff;
    z-index: 999;
    overflow: hidden;
    display: none;
}
.inner{
    /* width: 130%;
    height:130%;
    background-size: cover; */
}
.myalert{

}
</style>