<template>
 <div>
 <ul> 
   <ToDoItem 
     v-for= "todo of todos"
     v-bind:key="todo.id"
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

<style>
ul {
    list-style: none;
    margin: 0px auto;
    padding: 0px;
    width: 70%;
    

}
</style>