<script setup>
import { ref } from "vue";

const props = defineProps({
  taskTitle: String,
  editing: Boolean,
});

const emits = defineEmits(["toggleEdit", "updateTaskTitle", "delete"]);

const newTitle = ref(props.taskTitle);
</script>

<template>
  <li class="todoItem">
    <div class="left">
      <i class="fa-regular fa-circle"></i>

      <!-- Toggle between text and input field -->
      <span v-if="!props.editing" class="text">{{ props.taskTitle }}</span>
      <input v-else v-model="newTitle" @keyup.enter="$emit('updateTaskTitle', newTitle)" />
    </div>
    <!-- ./left -->

    <div class="right">
      <span class="edit-btn">
        <i @click="$emit('toggleEdit')" class="fa-solid fa-pen-to-square"></i>
      </span>

      <span @click="$emit('delete')" class="delete-btn">
        <i class="fa-solid fa-trash"></i>
      </span>
    </div>
    <!-- ./right -->
  </li>
</template>

<style scoped>
/* todoItem.css */
li.todoItem {
  display: flex;
  justify-content: space-between;
  margin: 10px 0;
  padding: 10px 5px;
  border-radius: 5px;
  border: 1px solid #ff0066;
  color: #000;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

li.todoItem:hover {
  border-color: purple;
}

.left i {
  margin-right: 5px;
  font-size: 20px;
}

.left {
  display: flex;
  justify-content: center;
  align-items: center;
}

.right span i {
  color: #000;
}

.right .delete-btn {
  margin-left: 20px;
}

.right .delete-btn i:hover {
  color: red;
}

.right .edit-btn i:hover {
  color: dodgerblue;
}
</style>