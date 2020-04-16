<template>
<main>


<!-- animate.css -->
     <!-- <transition enter-class="animated bounce"
     leave-to-class="animated fadeOut"
     > -->

    <transition name="myfade">
        <div v-if="toggle" class="myalert">Hi! I'm from vue!</div>
    </transition>
    <button @click="toggleModal">show alert</button>
</main>
</template>

<script>
export default {
    data(){
        return{
            toggle:false
        }
    },
    methods: {
        toggleModal(){
            this.toggle = !this.toggle;
        }
    }
}
</script>

<style>
*{
    transition: all 0.5s ease;
}
.myalert{
    position: fixed;
    left:50%;
    top:50%;
    transform:translate(-50%,-50%);
    background-color: #ccc;
    padding:20px;
    }
    .myfade-enter,.myfade-leave-to{
        /* opacity:0; */
        /* transform:scale(1.3) */
    }

    /* .v-enter  ----  .v-enter-active   ----  .v-enter-to
    .v-leave  ----  .v-leave-active  ---- .v-leave-to */
    
</style>