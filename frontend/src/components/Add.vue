<template>
    <Header />
    <h1 class="h1">Hello , Welcome to Add Restaurant page</h1>
</template>
<script>
import Header from './Header.vue';
export default {
    name: 'Add',
    mounted() {
        let user = localStorage.getItem('user-info')
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
    },
    components: {
        Header
    }
}
</script>
<style scoped>
.h1 {
    color:black;
}
</style>
