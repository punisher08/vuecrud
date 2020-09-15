<template>
  <div class="about">
  <EditTodo />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// import Header from "../components/layouts/Header.vue";
import EditTodo from '../components/EditTodo.vue'
export default {
  name: 'About',
  components:{
   EditTodo
  }
}
</script>