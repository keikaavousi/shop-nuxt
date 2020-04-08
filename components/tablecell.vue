<template>
    <td>{{txt}}
        <img :src="url">
        <slot></slot>
    </td>
</template>

<script>
export default {
    name:'tablecell',
    props:['txt','url']
}
</script>

<style>

</style>