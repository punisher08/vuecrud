<template>
  <div id="app">
    
    <!-- <Header /> -->
     
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos="todos"  v-on:del-todo="deleteTodo"/>
  </div> 
</template>
<script>
// import Header from "../components/layouts/Header";
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
// import axios from "axios"
// import HelloWorld from "./components/HelloWorld";
export default {
  name:'Home',
  components:{
    // HelloWorld,
    // Header,
    Todos,
    AddTodo
  },
  data(){
    return{
      todos: [
        {
          id:1,
          title:'One',
          completed:false
        },
        {
          id:2,
          title:'Two',
          completed:false
        },
        {
          id:3,
          title:'Three',
          completed:false
        },
      ]
    }
  },
  methods:{
    
    deleteTodo(id){
      // this.todos = this.todos.filter(todo => todo.id !==id)
      // axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      //   .then(response => {
      //     console.log(response)
        // })
          this.todos = this.todos.filter(todo => todo.id !==id)
        // .catch(error => console.log(error));
      
      // this.todos = this.todos.filter(todo => todo.id !== id);

      // axios.get(`http://myendpoint.com/v1/api/${todo.id}`)
      //       .then(response => {
      //           this.todo = 'something'
      //           alert('Todo Added')
      //           console.log(response)
      //         })
      //         .catch(err => {
      //           alert('something went wrong')
      //           console.log(err)
      //         })
      // try {
      //   var enpointResult = await axios.get(`http://myendpoint.com/v1/api/${todo.id}`);
      // } catch (error) {
      //   console.log(error)
      // }
      
      // console.log('delayed');

      
    },
    addTodo(myNewTodo){
    //  const{title,completed} = myNewTodo
    //  axios.post('https://jsonplaceholder.typicode.com/todos',{
    //    title,
    //    completed
    //  }).then(response => this.todos = [...this.todos, response.data])
    //  .catch(error => console.log(error))
      this.todos = [...this.todos, myNewTodo];
     
    }
  },
  // created(){
  //   axios.get('https://jsonplaceholder.typicode.com/todos?_limit=1').then(res => this.todos = res.data)
  //   .catch(error => console.log(error))
  // }
 

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
