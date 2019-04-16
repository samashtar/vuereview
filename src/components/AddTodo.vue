<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="add todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>


<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        //   id:
      };
    }
  }
};
</script>

<style scoped>
</style>
