<template>
  <p v-bind:class="{ 'is-complete' : todo.completed }">
    <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
    {{ todo.title }}
    <button class="round-button" v-on:click="$emit('del-todo', todo.id)">X</button>
  </p>
</template>

<script>
export default {
  name: "todo-item",
  props: {
    todo: Object
  },
  methods: {
    markComplete(event) {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
}

button {
  margin-left: 1rem;
}
</style>