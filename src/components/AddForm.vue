<template>
    <form @submit.prevent ="onSubmit">
        <input type="text" v-model="title">
        <button class='add'>Add new todo!</button>
    </form>
</template>

<script>
export default {
    name: "AddTodo",
    methods: {
        onSubmit(){
            if(this.title.trim()){
                const newTodo = {
                    id : Date.now(),
                    title : this.title,
                    completed : false
                }

                this.$emit('add-todo' , newTodo)
            }
        }
    } ,
    data(){
        return{
            title: ''
        }
    }
}   
</script>

<style  scoped>
    form{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    input{
        width: 60%;
        font-size: 18px;
        text-align: center;
        letter-spacing: .2em; 
    }
    .add{
        font-size: 18px;
        font-weight: 600;
        color: green;

        background-color: white;
        min-width: 35%;
    }
    .add:hover{
        background-color: green;
        color: white;
    }
</style>