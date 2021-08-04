<template>
  <div id="app">
   <h1> Todos apllication  </h1>
   <hr>
    <router-view/>

    <NavBar />
  </div>
</template>

<script>
import TodoList from '@/components/Todo'
import NavBar from '@/components/NavBar'

export default {
  name: 'App',
  methods: {
    removeTodo( idd ){
      this.todos = this.todos.filter(it => it.id != idd)
    },
    addTodo(newTodo){
      this.todos.push(newTodo)
    }
  },
  components: {
    TodoList ,
    NavBar
  }
}
</script>

<style scoped>
    h1{
      font-size: 120px;
      color: green;
      border: 2px crashed grey;
      text-align: center;
    }
</style>
