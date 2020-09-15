<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p><svg v-on:click="EditModal" width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-pencil-square mr-2" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
    <path d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456l-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"/>
    <path fill-rule="evenodd" d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"/>
    </svg>
    <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-justify mr-2" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
    <path fill-rule="evenodd" d="M2 12.5a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 0 1h-11a.5.5 0 0 1-.5-.5zm0-3a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 0 1h-11a.5.5 0 0 1-.5-.5zm0-3a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 0 1h-11a.5.5 0 0 1-.5-.5zm0-3a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 0 1h-11a.5.5 0 0 1-.5-.5z"/>
    </svg>{{todo.title}} </p>
    <button class="del btn btn-danger"  @click="$emit('del-todo',todo.id)" >delete</button>
  </div>
</template>


<script>
export default {
    name:'TodoItem',
    props:['todo'],
 
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed
            
        },
        EditModal: function(){
           console.log('click')
        }
     

    },

}
</script>
<style scoped>
.todo-item{
    background :#f4f4f4;
    padding :10px;
    border-bottom : 1px #ccc dotted;
    display: flex;
    justify-content: space-between;
}
.is-complete{
    text-decoration: line-through;
}



</style>
