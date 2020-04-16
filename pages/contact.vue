<template>
<main>
<form @submit="handleSubmit">
    <input type="text" v-model="name" placeholder="name" required>
    <input type="text" v-model="family" placeholder="family" required>
    <!-- <input type="password" pattern="[0-9]"> -->

    <input type="radio" value="man" v-model="gender">
    <input type="radio" value="woman" v-model="gender">

     <input type="checkbox" value="val1" v-model="chck">
     <input type="checkbox" value="val2" v-model="chck">

        <select v-model="personCity">
            <option value="-1">--please select--</option>
            <option v-for="(city,index) in cities" :key="index" :value="city">{{city}}</option>
        </select>

    <textarea v-model="msg"></textarea>

    <button ref="btn">send</button>
</form>
</main>
</template>

<script>
export default {
    data(){
        return{
           name:'' ,
           family:'',
           gender:'',
           chck:[],
           personCity:'',
           cities:['tehran','shiraz','esfahan'],
           msg:''
        }
    },
    methods: {
        handleSubmit(e){
            if(this.name!="" && this.family!="" && this.personCity=="-1"){

               // if(/[a-z]/.test(this.password))

            this.$refs.btn.disabled="disabled"
            e.preventDefault();
            let formd = {
                fname: this.name,
                lname: this.family,
                gender:this.gender
            }
            fetch('https://fakestoreapi.com/users',{
                method:'POST',
                body:JSON.stringify(formd)
            })
            .then(res=>res.json())
            .then(rs=>{
                console.log(rs)
                if(rs.status=="inserted"){
                    alert('Form submitted')
                }
            })
            console.log('form data',this.name,this.family,this.gender,this.personCity)
            }
            else{
                alert('all fields should be filled')
            }
        }
    },
}
</script>

<style>

</style>