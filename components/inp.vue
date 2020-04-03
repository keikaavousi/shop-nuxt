<template>
  <input type="number" :value="quantity" @click="handleNum">
</template>

<script>
export default {
    name:'inp',
    props:['quantity','id'],
    data(){
        return{
            quan:this.quantity,
            i:this.id
        }
    },
    methods: {
        handleNum(e){
            console.log(e.target.value,this.id)
        }
    },
}
</script>

<style>

</style>