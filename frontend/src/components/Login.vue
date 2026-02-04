<template>
    <img class="logo" src="../assets/resto.jpg">
    <h1 class="h1">Login Page</h1>
    <div class="Register">
        <input v-model="name" type="text" placeholder="Enter Name">
        <input v-model="password" type="password" placeholder="Enter Password">
        <button v-on:click="login">Login</button>
        <p>
            <router-link to="/signup">Sign Up</router-link>
        </p>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    name: 'Login',
    data() {
        return {
            name: '',
            password: ''
        }
    },
    methods: {
        async login() {
            let result = await axios.get(
                `http://localhost:3000/users?name=${this.name}&password=${this.password}`
            )
            if (result.status == 200 && result.data.length > 0) {
                alert("LogIn Succesfull")
                this.$router.push({ name: 'Home' })
                localStorage.setItem("user-info", JSON.stringify(result.data[0]))
            }
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info')
        if (user) {
            this.$router.push({ name: 'Home' })
        }
    }
}
</script>
<style>
.h1 {
    color: darkblue;
}

.logo {
    width: 200px;
}
</style>