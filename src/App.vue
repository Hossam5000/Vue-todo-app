<script setup>
import todoItem from "./components/todoItem.vue";

</script>

<template>
  <main class="main">
    the parent element
    <todoItem />
  </main>
</template>

<style scoped>
.main {
  background-color: green;
}
</style>