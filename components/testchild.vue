<template>
  <div>
    <h1>{{title}}</h1>
    <h2>{{subtitle}}</h2>
    <input v-model="mytitle">
    <button @click="$emit('handleClick')">click</button>
  </div>
</template>

<script>
export default {
  name: "child",
  props:['title','subtitle'],
  data(){
      return{
          mytitle:this.title,
          arr:[]
      }
  },
  asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
    
  },
  created() {
      fetch('efwf')
      .then(res=>res.json())
      .then(rs=>{
          arr=rs
      })
  },
  mounted() {
      
  },
  computed: {
        upper(){
            return{
                
            }
        }
  },
  methods: {
      handleClick(){

      }
  },
};
</script>

<style>
</style>