<template>
    <div>
        <AddTodo 
        v-on:add-todo='addTodo'
        />

        <select v-model="filter">
            <option value="all">All todso!</option>
            <option value="com">Only completed</option>
            <option value="not-com">Only not completed!</option>
        </select>

        <ul v-if="filterTodos.length">
            <TodoItem
                v-for="(todo , i) of filterTodos"
                v-bind:todo="todo"
                v-bind:index="i"
                v-on:remove-todo="removeTodo"  
            />
        </ul>
        <p
            v-else
            >No items!</p>
    </div>
</template>


<script>
    import TodoItem from '@/components/TodoItem'
    import AddTodo from '@/components/AddForm'

    export default {
        name : 'Todo',
        data(){
      return{
        todos : [
      {id : 1 , title : "I need to buy a bread!" , completed : false},
      {id : 2 , title : "I need to buy a oil!" , completed : false},
      {id : 3 , title : "I need to buy a some fruit!" , completed : false}
                ],
        filter: 'all'
                }    
            },
        methods:{
            removeTodo(id){
                this.todos = this.todos.filter( (item) => item.id!==id )
            },
            addTodo(newTodo){
                this.todos.push(newTodo)
            }
        },
        components: {
            TodoItem ,
            AddTodo
        },
        computed: {
            filterTodos(){
                if(this.filter === 'all'){
                    return this.todos
                }
                if(this.filter === 'com'){
                    return this.todos.filter(item => item.completed)
                }

                if(this.filter === 'not-com'){
                    return this.todos.filter( item => !item.completed )
                }
            }
        }
        
    }
</script>

<style >
    ul{
        display:flex;
        flex-direction: column;
        
        padding: 15px 10px;

        border: 3px solid blue;
    }

    p{
        text-align: center;
        color: red;
        font-size: 26px;
        letter-spacing: .4em;
    }
</style>