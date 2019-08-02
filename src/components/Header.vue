<template>
  <header class="text-center">
    <h3>A Todo App</h3>
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
header {
  background: rebeccapurple;
  margin: 1rem;
}

h3, a {
  color: white;
}
</style>