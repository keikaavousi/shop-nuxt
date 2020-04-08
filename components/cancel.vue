<template>
  <button @click="$emit('removeitem')">&times;</button>
</template>

<script>
export default {
    name:'cancel'
}
</script>

<style scoped>
    button{
        background-color: red;
        color:#fff;
        border:none;
    }
</style>