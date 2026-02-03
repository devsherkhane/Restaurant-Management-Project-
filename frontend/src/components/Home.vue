<template>
<h1 class="h1" >Hello , Welcome to  Home page</h1>
</template>
<script>
export default {
    name:'Home',
    mounted() {
        let user = localStorage.getItem('user-info')
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
    }
}
</script>
<style>
.h1{
    color: skyblue;
}
</style>
