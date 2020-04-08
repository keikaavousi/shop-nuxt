<template>
  <input type="number" v-model="quan" min="1" @change="handleNum">
</template>

<script>
export default {
    name:'inp',
    props:['quantity','id'],
    data(){
        return{
            quan : this.quantity,
            i : this.id
        }
    },
    methods: {
        handleNum(){
                let finded_index = this.$state.cart.findIndex(n=>{
                    return n.id == this.i
                })
                this.$state.cart[finded_index].quantity = this.quan
                console.log(this.$state.cart)
        }
    },
}
</script>

<style>

</style>