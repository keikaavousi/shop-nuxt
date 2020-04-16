<template>
<div>
  <input type="text" v-model="searchTxt" placeholder="searchproducts">
  <button @click="handleSearch">search</button>
  <ul>
    <li v-for="item in searched" :key="item.id">
      {{item.title}}
    </li>
  </ul>
</div>
</template>

<script>
export default {
name:'searchInput',
data() {
  return {
    searchTxt:'',
    searched:[]
  }
}, 
methods: {
  handleSearch(){
    // this.$state.products=this.$state.products.filter(n=>{
    //   return n.title.toLowerCase().includes(this.search.toLowerCase())
    // })
    fetch(`http://localhost:9000/products?search=${this.searchTxt}`)
    .then(res=>res.json())
    .then(rs=>{
      this.searched=rs
      this.searchTxt=""
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