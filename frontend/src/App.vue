<template>
  <router-view />
</template>


<script>
export default {
  name: 'App',

}
</script>
<style>
.Register input ,.login input{
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

.Register button ,.login input{
    width: 320px;
    color: #fff;
    background-color: skyblue;
    cursor: pointer;
}
</style>
