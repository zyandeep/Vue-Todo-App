<template>
  <div id="todos">
    <div v-for="todo in todos" v-bind:key="todo.id">
      <todo-item v-bind:todo="todo" @del-todo="$emit('del-todo', todo.id)"/>
    </div>
    <h5 v-if="todos.length === 0">
      No Todo exist! 
    </h5>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "todos",
  props: {
    todos: Array
  },
  components: {
    TodoItem
  }
};
</script>

<style scoped>
</style>
