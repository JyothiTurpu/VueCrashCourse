<template>
  <div id="app">
    <Header />
    <AddToDo v-on:add-todo="addToDo" />
    <ToDos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>


<script>
import axios from 'axios';
import ToDos from './components/ToDos';
import Header from './components/Layout/Header';
import AddToDo from './components/AddToDo';

export default {
  name: 'App',
  components: {
    ToDos,
    Header, 
    AddToDo
  },

  data() {
    return {
      todos: []
      }
    },

  methods: {

    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(response => {
        console.log(response);
        this.todos = this.todos.filter(todo => todo.id !== id);
      })
      .catch(error => {
        console.log(error);
      });
    },


    addToDo(newToDo) {
      const { title, completed } = newToDo;

      axios.post('https://jsonplaceholder.typicode.com/todos',{title, completed})
      .then(response => {
        console.log(response);
        this.todos = [...this.todos, response.data];
      })
      .catch(error => {
        console.log(error);
      });
    }
    
  },

  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(response => {
      this.todos = response.data;
    })
    .catch(error => {
      console.log(error);
    });
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


.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
  
</style>
