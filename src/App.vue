<template>
  <div class="small-container">
    <Header />

    <router-view />
  </div>
</template>

<script>
import Header from "./components/Header";

export default {
  name: "app",
  components: {
    Header
  }
};
</script>


<style scoped>
</style>
