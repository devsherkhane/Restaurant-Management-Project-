<template>
    <Header />
    <h1 class="h1">Hello , Welcome to Update Restaurant page</h1>
     <form class="add">
        <input type="text" placeholder="Enter name" v-model="restaurant.name" name="name">
        <input type="text" placeholder="Enter Contact No" v-model="restaurant.contact" name="contact">
        <button type="button" v-on:click="updateRest">Update Restaurant</button>
    </form>
</template>
<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
    name: 'Update',
     data() {
        return {
            restaurant: {   
                name: '',
                contact: ''
            }
        }
    },
    async mounted() {
        let user = localStorage.getItem('user-info')
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
        const result =await axios.get("http://localhost:3000/restaurants/"+this.$route.params.id)
        this.restaurant=result.data
    },
    components: {
        Header
    },
    methods:{
        async updateRest(){
            const result = await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
                    name:this.restaurant.name,
                    contact:this.restaurant.contact
                })
                if(result.status==200){
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
