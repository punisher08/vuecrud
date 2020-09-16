<template>
  <div class="container">
    <br />
    <form v-on:submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="title" class="form-control" />
      <br />
      <textarea
        type="text"
        v-model="description"
        name="title"
        placeholder="description"
        class="form-control"
      />
      <br />
      <input type="submit" value="submit" class="btn btn-primary add-btn" />
    </form>
  </div>
</template>
<script>
// import uuid from 'uuid';
// import { v4 as uuidv4 } from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
      description: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id:uuidv4(),
        title: this.title,
        description: this.description,
        completed: false,
      };
      // console.log(newTodo)
      this.$emit("add-todo", newTodo);
      this.title = "";
      this.description = "";
    },
  },
};
</script>
<style scoped>
.add-btn {
  float: right;
}
</style>