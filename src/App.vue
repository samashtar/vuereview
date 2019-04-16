<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"></Todos>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import Header from "./components/layout/Header";
export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  },
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
