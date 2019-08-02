<template>
  <div id="add-todo">
    <form @submit.prevent="addTodo">
      <input 
        type="text" 
        placeholder="add a todo item..."
        v-model="title" 
        :class="{ 'has-error' : error }" 
        @focus="clearError"/>

      <input  class="accent-button round-button" type="submit" value="Add" />
    
    </form>
  </div>
</template>

<script>
export default {
  name: "add-todo",
  data() {
    return {
      title: "",
      error: false,
    }
  },
  methods: {
    addTodo() {
      if (this.title.trim().length === 0) {
        this.error = true;
        return;
      }

      // emit the event to parent
      const newTodo = {
        title: this.title,
        completed: false
      };
      this.$emit("add-todo", newTodo);

      // clear state/date
      this.title = "";
      this.error = false;

    },
    clearError() {
      this.error = false;
    },
  }
};
</script>

<style scoped>

</style>