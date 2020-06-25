<template>
  <div id="app">
    
   <h1>To do App</h1>
   <hr>
   <ToDoList
   v-bind:todos="todos"
   @remove-todo="removeTodo"
   />
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList';
export default {
  name: 'app',
  data() {
   return {
     todos: [
       {id: 1,  title: 'Kупить хлеб', completed: false},
       {id: 2,  title: 'Kупить масло', completed: false},
       {id: 3,  title: 'Kупить сало', completed: false}

     ]
   }
  },
  methods: {
   removeTodo(id){
     this.todos= this.todos.filter(t => t.id !==id)

   }
  },
  components: {
    ToDoList
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
