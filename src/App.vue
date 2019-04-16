<template>
  <div id="app">
    <Todos></Todos>
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "app",
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "todo one",
          completed: false
        },
        {
          id: 2,
          title: "todo two",
          completed: true
        },
        {
          id: 3,
          title: "todo three",
          completed: false
        }
      ]
    };
  }
};
</script>

<style>
</style>
