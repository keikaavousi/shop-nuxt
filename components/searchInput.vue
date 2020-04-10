<template>
  <input type="text" v-model="search" placeholder="searchproducts" @keyup="handleSearch"/>
</template>

<script>
export default {
name:'searchInput',
data() {
  return {
    search:''
  }
}, 
methods: {
  handleSearch(){
    this.$state.products=this.$state.products.filter(n=>{
      return n.title.toLowerCase().includes(this.search.toLowerCase())
    })
  }
},
}
</script>

<style>
  input{
    width:100%;
    display: block;
    margin-bottom: 30px;
  }
</style>