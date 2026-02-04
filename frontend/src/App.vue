<template>
  <router-view />
</template>


<script>
export default {
  name: 'App',

}
</script>
<style>
.Register input ,.login input ,.add input{
    width: 300px;
    height: 30px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid darkblue;
    color: black;
    background-color: #fff;
}
body{
  padding: 0;
  margin: 0;
}
.Register button ,.login input ,.add button{
    width: 320px;
    color: #fff;
    background-color: darkblue;
    cursor: pointer;
}
</style>
