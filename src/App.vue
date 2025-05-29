<script setup>
// imports
import { ref } from "vue";
import { watch } from "vue";
import { onMounted } from "vue";

import todoItem from "./components/todoItem.vue";

// cons & vars
const inputNewTodo = ref("");
const newTime = ref("");
let todos = ref([]);
const age = ref(0);

// functions
function addTodo() {
  const todo = {
    text: inputNewTodo.value,
    completed: false,
  };

  todos.value.push(todo);
  save();
  inputNewTodo.value = "";
}

function save() {
  localStorage.setItem("todos", JSON.stringify(todos.value));
};

function load() {
  todos.value = JSON.parse(localStorage.getItem("todos") || []);
};

function deleteTodo(index) {
  todos.value.splice(index, 1);
  save();
};

function increase(n) {
  n += 1;
  console.log(`number of counts until now ${n}`);
}

// watchers
watch(todos, () => {
  localStorage.setItem("todos", JSON.stringify(todos.value));
}, { deep: true });

watch(age, (newValue, oldValue) => {
  console.log(`the old value is ${oldValue} the new value is ${newValue}`)
});

// life-cycle-hooks
onMounted(() => {
  load();
}
);
</script>

<template>
  <h2 class="title">TODO APP</h2>
  <button @click="age++">increment</button>
  {{ age }}
  <div class="app-container">
    <div class="head-container">
      <input @keyup.enter="addTodo" v-model="inputNewTodo" placeholder="Add new todo" />
      <button @click="addTodo">ADD</button>
    </div>
    <!--./head-container-->

    <!-- todo list -->
    <ul class="todoList">
      <todoItem v-for="(todo, index) in todos" :key="index" :task-title="todo.text" @delete="deleteTodo(index)"
        @cons="increase" />
    </ul>

  </div>
  <!--./app-container-->

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
  /* border: 1px solid #000; */
  margin-top: 30px;
  padding: 0 10px;
}

ul.todo-list li {
  list-style-type: none;
}
</style>
