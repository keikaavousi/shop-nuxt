<template>
    <td>{{txt}}
        <slot></slot>
    </td>
</template>

<script>
export default {
    name:'tablecell',
    props:['txt']
}
</script>

<style>

</style>