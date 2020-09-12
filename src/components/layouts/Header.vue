<template>
<div class="header">
    <h1>TodoList</h1>
     <div class="home">
      <router-link to="/" class="home">Home</router-link>
      <router-link to="/about" class="about">About</router-link>
    </div>


</div>
</template>
<script>
export default {
    name: 'Header'
}
</script>
<style scoped>
.header{
    text-align: center;
    background-color: #333;
    color: white;
}
.home{
  color: #fff;
  text-decoration: none;
  padding-left: 5px;
}
.home:hover{
  color: #42b983;
}
.about{
  color: #fff;
  text-decoration: none;
    padding-left: 5px;
}
.about:hover{
   color: #42b983;
}


</style>