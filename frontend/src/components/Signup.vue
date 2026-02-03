<template>
    <img class="logo" src="../assets/resto.jpg">
    <h1 class="Signup">Sign Up</h1>
    <div class="Register">
        <input v-model="name" type="text" placeholder="Enter Name">
        <input v-model="email" type="text" placeholder="Enter Enail">
        <input v-model="password" type="password" placeholder="Enter Password">
        <button v-on:click="SignUp">Sign Up</button>
        <p>
            <router-link to ="/login">Login</router-link>
        </p>
    </div>
</template>
<script>
import axios from 'axios';
import { RouterLink } from 'vue-router';
export default {
    name: 'Signup',
    data() {
        return {
            name: '',
            email: '',
            password: ''
        }
    },
    methods: {
        async SignUp() {
            let result = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password
            })
            if (result.status == 201) {
                alert("Sign Up Done")
                this.$router.push({ name: 'Home' })
                localStorage.setItem("user-info", JSON.stringify(result.data))
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
.Signup {
    color: skyblue;
}

.logo {
    width: 200px;
}

.Register input {
    width: 300px;
    height: 30px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
    color: black;
    background-color: #fff;
}

.Register button {
    width: 320px;
    color: #fff;
    background-color: skyblue;
    cursor: pointer;
}
</style>