<template>
 <div class="container-fluid">
    <main>
  <searchInput/>
  <ul>
      <li v-for="product in this.$state.products" :key="product.id">
            <h2>{{product.title}}</h2>
      </li>
  </ul>
    </main>
 </div>
</template>

<script>
import searchInput from '../components/searchInput'
export default {
    components:{
        searchInput
    }
}
</script>

<style>

</style>