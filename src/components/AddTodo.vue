<template>
    <div class="container"><br>
        <form v-on:submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="title" class="form-control" />
            <input type="text" v-model="description" name="title" placeholder="description" class="form-control"/>
            <input type="submit" value="submit" class="btn">
        </form>
    </div>
</template>
<script>
// import uuid from 'uuid';
// import { v4 as uuidv4 } from 'uuid';
export default {
    name: 'AddTodo',
    data(){
        return{
            title:'',
            description:''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                // id:uuidv4(),
                title: this.title,
                description:this.description,
                completed: false
            }
            // console.log(newTodo)
            this.$emit('add-todo',newTodo);
             this.title = '';
             this.description='';
        }
    }
}
</script>
<style scoped>
form{
    display: flex;
}
input[type="text"]{
flex:10;
padding: 5px;
}
input[type="submit"]{
flex:2;

}
.btn{
    background: rgb(26, 139, 204);
    display: inline-block;
    border: none;
    color: white;
    padding: 7px 20px;
    cursor: pointer;
}
.btn:hover{
    background: rgb(101, 110, 116);
}
</style>