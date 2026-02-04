<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="add">Add Restaurant</router-link>
        <a v-on:click="logout">Logout</a>
    </div>
</template>
<script>

export default {
    name: 'Header',
    methods: {
        logout() {
            localStorage.clear();
            this.$router.push({ name: 'Login' })
        }
    }
}
</script>
<style>
.nav {
    background-color: darkblue;
    overflow: hidden;
}

.nav a {
    float: left;
    color: #fff;
    text-align: center;
    padding: 10px 14px;
    text-decoration: none;
    font-size: 16px;
    margin-right: 5px;
}

.nav a:hover {
    background-color: #fff;
    color: black;
}
</style>