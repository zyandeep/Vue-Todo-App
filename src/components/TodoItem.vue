<template>
  <div id="todo-item">
    <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
    <span v-bind:class="{ 'is-complete' : todo.completed }"> {{ todo.title }} </span>
    <button class="round-button" v-on:click="deleteTodo">X</button>
    <p v-if="isDeleted">
      <cite>{{ msg }}</cite>
    </p>
  </div>
</template>

<script>
export default {
  name: "todo-item",
  props: {
    todo: Object
  },
  data() {
    return {
      msg: "deleting...please wait",
      isDeleted: false,
    }
  },
  methods: {
    markComplete(event) {
      this.todo.completed = !this.todo.completed;
    },
    deleteTodo() {
      this.isDeleted = true;
      this.$emit('del-todo', this.todo.id);
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