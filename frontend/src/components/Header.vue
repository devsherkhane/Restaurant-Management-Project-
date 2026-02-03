<template>
    <div class="nav">
        <a href="home">Home</a>
        <a href="home">Add Restaurant</a>
        <a href="home">Update Restaurant</a>
        <a href="home">Logout</a>
    </div>
</template>
<script>
export default{
    name:'Header'
}
</script>
<style>
.nav{
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
.nav a:hover{
    background-color: #fff ;
    color: black;
}
</style>