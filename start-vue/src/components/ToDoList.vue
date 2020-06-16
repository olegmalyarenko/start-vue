<template>
 <div>
 <ul> 
   <ToDoItem 
     v-for= "todo of todos"
     v-bind:todo="todo"
   />
 
 </ul>
 </div>
</template>

<script> 
import ToDoItem from '@/components/ToDoItem'
export default {
    props: ['todos'],
    components: {
    ToDoItem
  }
}
</script>

<style></style>