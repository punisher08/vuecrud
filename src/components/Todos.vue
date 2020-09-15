<template>
    <div class="container">
        <div>
        <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
    </div>

</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    name:'Todos',
    props:['todos'],
    components:{
        TodoItem
    },
    data(){
        return{
            something:'someone'
        }
    }
}
</script>

<style scoped>


</style>