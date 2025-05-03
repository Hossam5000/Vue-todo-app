<script setup>
// imports
import { ref } from 'vue';
import todoItem from './components/todoItem.vue'

// cons & vars
const inputNewTodo = ref("");

// functions

</script>

<template>
  new app
  <div class="head-container">
    <input v-model="inputNewTodo" placeholder="Add new todo">
    <button>ADD</button>
  </div><!--./container-->

  <!-- todo list -->
  <ul class="todoList">
    <todoItem />
  </ul>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.head-container {
  background: purple;
  padding: 3px;
}

ul {
  border: 1px solid #000;
}

ul li {
  list-style-type: none;
}
</style>