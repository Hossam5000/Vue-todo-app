<script setup>
import { ref, onMounted } from "vue";
import todoItem from "./components/todoItem.vue";

const inputNewTodo = ref("");
let todos = ref([]);

function addTodo() {
  if (!inputNewTodo.value.trim()) return; // Prevent empty todos

  const todo = {
    id: Date.now(), // Unique identifier
    text: inputNewTodo.value,
    completed: false,
    editing: false, // Track edit mode
  };

  todos.value.push(todo);
  save();
  inputNewTodo.value = "";
}

function save() {
  localStorage.setItem("todos", JSON.stringify(todos.value));
}

function load() {
  todos.value = JSON.parse(localStorage.getItem("todos") || "[]");
}

function deleteTodo(index) {
  todos.value.splice(index, 1);
  save();
}

onMounted(() => {
  load();
});
</script>

<template>
  <h2 class="title">TODO APP</h2>
  <div class="app-container">
    <div class="head-container">
      <input @keyup.enter="addTodo" v-model="inputNewTodo" placeholder="Add new todo" />
      <button @click="addTodo">ADD</button>
    </div>
    <!-- ./head-container -->

    <!-- todo list -->
    <ul class="todoList">
      <todoItem v-for="todo in todos" :key="todo.id" :task-title="todo.text" :editing="todo.editing"
        @toggleEdit="todo.editing = !todo.editing"
        @updateTaskTitle="(newTitle) => { todo.text = newTitle; todo.editing = false; save(); }"
        @delete="deleteTodo(todos.indexOf(todo))" />
    </ul>
  </div>
  <!-- ./app-container -->
</template>

<style scoped>
/* App.css */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h2 {
  margin: 30px auto 10px;
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
  margin-top: 30px;
  padding: 0 10px;
}

ul.todo-list li {
  list-style-type: none;
}
</style>