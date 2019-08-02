<template>
  <div>
    
    <add-todo @add-todo="addTodo" />

    <todos v-bind:todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";


export default {
  name: "home",
  components: {
    Todos,
    AddTodo
  },
  methods: {
    deleteTodo(id) {
      // make API call to delete the todo

      fetch(`https://jsonplaceholder.typicode.com/users/${id}`, {
        method: "DELETE"
      })
      .then(response => {
        if (response.status == 200) {
          // todo deleted
          this.todos = this.todos.filter(t => t.id !== id);
        }
      })
      .catch(error => console.log(error));
    },
    addTodo(todo) {
      const id = this.todos.length > 0 ? this.todos.length + 1 : 1;
      todo = { id, ...todo };

      // this.todos.push(todo);

      this.todos = [...this.todos, todo];
    }
  },
  data() {
    return {
      todos: []
    };
  },
  created() {
    const promise = fetch("https://jsonplaceholder.typicode.com/todos?_limit=5");
    promise.then(res => {
      console.log(res);
      return res.json();
    })
    .then(data => this.todos = [ ...data ] )
    .catch(err => console.log(err));
  }
};
</script>

<style scoped>
</style>
