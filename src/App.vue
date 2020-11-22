<template>
  <div id="app">
    <ToDos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>

import ToDos from './components/ToDos';

export default {
  name: 'App',
  components: {
    ToDos
  },

  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo One',
          completed: false
        },
        {
          id: 2,
          title: 'Todo Two',
          completed: true
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: false
        }
        ]
      }
    },

  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  }

body {
font-family: Arial, Helvetica, sans-serif;
line-height: 1.4;
  }
  
</style>
