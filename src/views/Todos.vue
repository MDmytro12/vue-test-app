<template>
  <div id="app">
   <h1> Todo`s list :  </h1>
   <hr>
   <TodoList 
    v-bind:todos="todos"
    @removeTodo='removeTodo'
    @addTodo='addTodo'
   />

    <router-view/>

  </div>
</template>

<script>
import TodoList from '@/components/Todo'

export default {
  name: 'App',
  data(){
      return{
        todos : [
      {id : 1 , title : "I need to buy a bread!" , completed : false},
      {id : 2 , title : "I need to buy a oil!" , completed : false},
      {id : 3 , title : "I need to buy a some fruit!" , completed : false}
    ]
      }    
  },
  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10').
    then(res => res.json()).
    then(json => this.todos = json )
  },
  methods: {
    removeTodo( idd ){
      this.todos = this.todos.filter(it => it.id != idd)
    },
    addTodo(newTodo){
      this.todos.push(newTodo)
    }
  },
  components: {
    TodoList
  }
}
</script>

<style>
  #app{
    width: 1000px;
    margin: 0 auto;
    padding: 0;

    display: block;
  }
</style>