<template>
  <nav class="col-md-12">
    <Logo/>
    <ul>
      <li>
        <nuxt-link to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/cart">Cart</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/invoice">Invoice</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/">Profile</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/search">Search</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/contact">Contact</nuxt-link>
      </li>
      <li>
          <nuxt-link to="/">
                <span class="badge badge-success">{{this.$state.cart.length}}</span>
          </nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import Logo from '~/components/Logo.vue'
  export default {
      name:'Navigation',
       components: {
        Logo
        }
  }
</script>

<style scoped>
    nav{
        background-color: #f5f5f5;
        text-align: center;
        position: fixed;
        left:0;
        right: 0;
        top:0;
        padding: 20px;
        border-bottom:1px solid rgba(123, 123, 123, 0.3);
    }
    nav ul{
        width:90%;
        display: flex;
        justify-content: space-evenly;
        margin:0 auto
    }
    nav li{
        list-style-type:none
    }
    nav a{
        text-decoration: none;
        color:#000;
        padding:5px
    }
</style>
