<template>
  <div id="app">
    <Header />
    <router-view/>
</div>
  
</template>
<script>
import Header from './components/layouts/Header.vue'

export default {
  name:'App',
  // props:todos,
  components:{
    Header
  }
}
</script>
<style scoped>
.body{
  background-color: thistle;
}
</style>