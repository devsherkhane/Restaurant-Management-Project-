<template>
    <Header />
    <h1 class="h1">Add Restaurant page</h1>
    <form class="add">
        <input type="text" placeholder="Enter name" v-model="restaurant.name" name="name">
        <input type="text" placeholder="Enter Contact No" v-model="restaurant.contact" name="contact">
        <button type="button" v-on:click="addRest">Add Restaurant</button>
    </form>
</template>
<script>
import axios from 'axios';
import Header from './Header.vue';
export default {
    name: 'Add',
    data() {
        return {
            restaurant: {   
                name: '',
                contact: ''
            }
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info')
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
    },
    components: {
        Header
    },
    methods:{
         async addRest(){
                const result = await axios.post("http://localhost:3000/restaurants",{
                    name:this.restaurant.name,
                    contact:this.restaurant.contact
                })
                if(result.status==201){
                    this.$router.push({name:'Home'})
                }
        }
    }
}
</script>
<style scoped>
.h1 {
    color: black;
}
</style>
