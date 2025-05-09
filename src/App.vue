<script setup>
// imports
import { ref } from "vue";
import todoItem from "./components/todoItem.vue";

// cons & vars
const inputNewTodo = ref("");

// functions
</script>

<template>
  <h2 class="title">TODO APP</h2>
  <div class="app-container">
    <div class="head-container">
      <input v-model="inputNewTodo" placeholder="Add new todo" />
      <button>ADD</button>
    </div>
    <!--./head-container-->
    <!-- todo list -->
    <ul class="todoList">
      <todoItem />
      <todoItem />
      <todoItem />
    </ul>
  </div>
  <!--./app-container-->

  <!--./container-->
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h2 {
  margin: 10px auto;
  text-align: center;
}

.head-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #000;
  border-radius: 30px;
  padding: 3px;
}

.head-container input {
  width: 100%;
  padding-left: 10px;
  background: none;
}

.head-container button {
  padding: 10px 30px;
  border-radius: 30px;
  background: #ff0066;
  color: #fff;
  cursor: pointer;
}

.head-container input,
.head-container button {
  outline: none;
  border: none;
}

ul.todoList {
  /* border: 1px solid #000; */
  margin-top: 10px;
  padding: 0 10px;
}

ul.todo-list li {
  list-style-type: none;
}
</style>
