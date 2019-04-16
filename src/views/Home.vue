<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"></Todos>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    //delete
    deleteTodo(id) {
      fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, {
        method: "delete"
      })
        .then(res => res.json())
        .then(data => (this.todos = this.todos.filter(todo => todo.id !== id)));
    },
    //post
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      fetch("https://jsonplaceholder.typicode.com/todos", {
        method: "POST",
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        body: JSON.stringify({ title, completed })
      })
        .then(res => res.json())
        .then(data => (this.todos = [...this.todos, data]));
    }
  },
  // get
  //component did mount
  created() {
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then(res => res.json())
      .then(data => (this.todos = data));
  }
};
</script>

<style>
</style>
