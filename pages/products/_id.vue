<template>
  <div class="details-head ">
      <div class="detail-img">
          <img :src="`${product.image}`"  @mousemove="getPos" @mouseenter="modalShow" @mouseleave="closeModal">
      </div>
      <div class="detail-info">
          <div class="detail-title">
          <h3>{{product.title}}</h3>
      </div>
      <div class="detail-desc">
          <p>{{product.description}}.</p>
      </div>
      <div class="detail-price">
          <h5>{{product.price}}$</h5>
      </div>
      <div class="detail-cat">
          <h5>{{product.category}}</h5>
      </div>
      <button class="btn btn-dark" @click="addtocart()" >Add to cart</button>
      </div>
      <div class="detail-modal" ref="modali">
          <img  ref="inner">
      </div>
  </div>
</template>

<script>
export default {
asyncData(context) {
    return fetch(`https://fakestoreapi.herokuapp.com/products/${context.params.id}`)
    .then(res=>res.json())
    .then(product=>{
        // console.log(product)
        return{
            product
        }
    })
},
methods:{
    addtocart(){
        // console.log(this.$state.cart)
        this.$state.cart=[...this.$state.cart,this.product]
    },
   modalShow(){
       this.$refs.modali.style.display="block"
       this.$refs.inner.src=this.product.image

   },
   getPos(e){
       console.log(e)

       let modalHeight=this.$refs.modali.offsetHeight
       let modalWidth=this.$refs.modali.offsetWidth

    let x=-Math.round((e.offsetX-modalWidth/2)*(2))
    let y=-Math.round((e.offsetY-modalHeight/2)*(2))
       this.$refs.inner.style.transform=`translate(${x}px,${y}px)`
   },
   closeModal(e){

        this.$refs.modali.style.display='none'
   }

},
}
</script>

<style scoped>

.details-head{
    margin-top: 150px;
    overflow: hidden;

}
.detail-info{
    height: auto;
    width: 1000px;
    overflow-x: hidden;
    overflow-y: hidden;
    border: 1px solid lightgrey;
    text-align: center;
    padding: 85px 25px 85px 25px;
    margin-top: -420px;
    margin-left: 550px;
    border-radius: 50px;

}
@media only screen and (max-width:767px){
    .detail-info{
    height: 500px;
    width: 400px;
    overflow: hidden;
    border: 1px solid lightgrey;
    text-align: center;
    padding: 85px 25px 85px 25px;
    margin-top: 20px;
    margin-left: 30px;
    border-radius: 50px;
    }
    .detail-img img{
        margin-left: -15px;
        
    }
    .detail-modal{

     display: none;
    }

}
 .detail-modal{
     position: absolute;
     width: 40%;
     height: 350px;
     top: 50%;
     left: 70%;
     transform: translate(-50%,-50%);
     background-color: white;
     display: none;
     overflow: hidden;
 }

    
    

.detail-img img{
    width: 500px;
    height: 500px;
}

.detail-img {
   margin-left: 10px;
}
</style>