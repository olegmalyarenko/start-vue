<template>
  <div>
    
   <h2>To do App</h2>
   <router-link to="/">Home</router-link>
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