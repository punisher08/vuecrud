<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">{{todo.title}}
        </p>
        <button class="del" @click="$emit('del-todo',todo.id)" >delete</button>
    </div>
</template>


<script>
export default {
    name:'TodoItem',
    props:['todo'],
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed
            
        }
    }
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
.del{
    margin: 20px;;
    max-height: 20px;
}


</style>