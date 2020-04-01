<template>
  <div class="container-fluid">
      <Card :product="myproduct" />
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
      }
    }
  }
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
</style>
