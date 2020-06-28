<template>
  <div>
    
   <h2>To do App</h2>
   <router-link to="/">Home</router-link>
   <AddToDo
    @add-todo="addTodo"
   />
   <select f-mpdel="filter">
     <option value="all">All</option>
     <option value="completed">Completed</option>
     <option value="not-completed">Not Completed</option>
   </select>
   <hr>
   <Loader v-if="loading"/>
   <ToDoList
   v-else-if="filteredTodos.length"
   v-bind:todos="filteredTodos"
   @remove-todo="removeTodo"
   />

   <p v-else>Nothing to do!</p>
  </div>
  
</template>

<script>
import ToDoList from '@/components/ToDoList';
import AddToDo from '@/components/AddToDo';
import Loader from '@/components/Loader';
export default {
  name: 'app',
  data() {
   return {
     todos: [],
     loading: true,
     filter: 'all'
   }
  },
  mounted(){
   fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
  .then(response => response.json())
  .then(json => {
      setTimeout(() => {
        this.todos = json
        this.loading = false
      }, 30000)
 
  })

  },
  computed: {
    filteredTodos() {
        

        if (this.filter === 'completed'){
          return this.todos.filter(t => t.completed)
        } 

        if (this.filter === 'completed'){
          return this.todos.filter(t => !t.completed)
        }
         
         return this.todos;
    }
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
    AddToDo,
    Loader
  }
}
</script>