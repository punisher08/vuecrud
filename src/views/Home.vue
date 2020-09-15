<template>
  <div id="app">
    
    <!-- <Header /> -->
     
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos="todos"  v-on:del-todo="deleteTodo"/>
  </div> 
</template>
<script>

import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios"

export default {
  name:'Home',
  components:{
    Todos,
    AddTodo
  },
  data(){
    return{
      todos: []
    }
  },
  methods:{
    
    deleteTodo(id){
  
      axios.delete(`http://127.0.0.1:8000/api/todo/delete/${id}`)
        .then(response => {
          console.log(response)
        })
    },
    addTodo(myNewTodo){
     const{title,description} = myNewTodo
     axios.post('http://127.0.0.1:8000/api/todo/create',{
       title,
       description
     }).then(response => this.todos = [...this.todos, response.data])
     .catch(error => console.log(error))
    }
  },
  created(){
    axios.get('http://127.0.0.1:8000/api/todos').then(res => {
      this.todos = res.data.data
      })
    .catch(error => console.log(error))
  }
 

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

</style>
