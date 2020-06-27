<template>
  <div id="app">
    
   <h1>To do App</h1>
   <AddToDo
    @add-todo="addTodo"
   />
   <hr>
   <ToDoList
   v-bind:todos="todos"
   @remove-todo="removeTodo"
   />
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList';
import AddToDo from '@/components/AddToDo';
export default {
  name: 'app',
  data() {
   return {
     todos: []
   }
  },
  mounted(){
   fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
  .then(response => response.json())
  .then(json => this.todos = json)
  },
  methods: {
   removeTodo(id){
     this.todos= this.todos.filter(t => t.id !==id)

   },
   addTodo(todo) {
    this.todos.push(todo)

   }
  },
  components: {
    ToDoList,
    AddToDo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
