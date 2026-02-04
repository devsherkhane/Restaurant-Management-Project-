<template>
    <Header />
    <h1 class="h1">Hello {{ name }} , Welcome to Home page</h1>
    <h2 class="h2">Restaurant List</h2>
    <table class="table" border="1px">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>
                <router-link :to="'/update/' + item.id"">Update</router-link>
                <button class="delbtn" v-on:click=" deleteRest(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>
<script>
import axios from 'axios';
import Header from './Header.vue';
export default {
    name: 'Home',
    async mounted() {
       this.loadData()
    },
    components: {
        Header
    },
    data() {
        return {
            name: '',
            restaurants: []
        }
    },
    methods: {
        async deleteRest(id) {
            let result = await axios.delete("http://localhost:3000/restaurants/" + id)
            if (result.status == 200) {
                this.loadData()
            }
        },
        async loadData() {
            let user = localStorage.getItem('user-info')
            this.name = JSON.parse(user).name
            if (!user) {
                this.$router.push({ name: 'Signup' })
            }
            let result = await axios.get("http://localhost:3000/restaurants")
            this.restaurants = result.data
        }
    }
}
</script>
<style scoped>
.h1 {
    color: black;
}

.h2 {
    color: black;
    text-align: left
}

.table {
    width: 500px;
    height: 40px;
    color: black;
}
.delbtn{
    height: 40px;
    margin-left: 10px;
    background-color: red;
}
</style>
