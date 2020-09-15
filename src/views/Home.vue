<template>
  <div id="app">
    <!-- <Header /> -->

    <AddTodo v-on:add-todo="addTodo" />
    <Todos :todos="todos" v-on:del-todo="deleteTodo" v-on:edit-todo="editTodo"></Todos>
    <Modal v-if="showModal" @close="showModal = false" v-on:save="saveData">
      <div slot="body">
        <form>
          <input type="text" name="title" v-model="selectedTodo.title" />
          <input type="text" name="description" v-model="selectedTodo.description" />
        </form>
      </div>
      <h3 slot="header">custom header</h3>
    </Modal>
  </div>
</template>
<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import Modal from "../components/Modal";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
    Modal,
  },
  data() {
    return {
      todos: [],
      showModal: false,

      selectedTodo: {
        title: "",
        description: "",
      },
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`http://127.0.0.1:8000/api/todo/delete/${id}`)
        .then((response) => {
          this.todos = this.todos.filter((todo) => todo.id !== id);
          console.log(response);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    addTodo(myNewTodo) {
      const { title, description } = myNewTodo;
      axios
        .post("http://127.0.0.1:8000/api/todo/create", {
          title,
          description,
          //  }).then(response => this.todos = [...this.todos, response.data])
        })
        .then((response) => (this.todos = [...this.todos, response.data.info]))
        .catch((error) => console.log(error));
    },
    editTodo(todoId) {
      console.log(todoId);
      this.showModal = true;

      this.todos.map((todo) => {
        if (todo.id == todoId) {
          this.selectedTodo.title = todo.title;
          this.selectedTodo.description = todo.description;
        }
      });
    },
    // showTodo(to_id) {
    //   console.log(to_id);
    // },
    saveData() {
      //
      console.log(this.selectedTodo.title, this.selectedTodo.description);
    },
  },
  created() {
    axios
      .get("http://127.0.0.1:8000/api/todos")
      .then((res) => {
        this.todos = res.data.data;
      })
      .catch((error) => console.log(error));
  },
};
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
