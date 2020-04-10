<template>
    <child title="hello" subtitle="world" @handleClick="myclick" />
</template>

<script>
import child from './testchild'
export default {
    components:{
        child
    },
    props:['handleClick'],
    methods: {
        myclick(){
            
        }
    },
}
</script>

<style>

</style>