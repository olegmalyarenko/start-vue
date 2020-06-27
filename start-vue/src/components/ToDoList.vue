import Vue from 'Vue';

<template>
 <div>
 <ul> 
   <ToDoItem 
     v-for= "(todo, i) of todos"
     v-bind:key="todo.id"
     v-bind:todo="todo"
     v-bind:index="i"
     v-on:remove-todo="removeTodo"
     
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
  },
  methods: {
    removeTodo(id) {
     this.$emit('remove-todo', id)
    }
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