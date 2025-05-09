<script setup></script>

<template>
  <li class="todoItem">
    <div class="left">
      <i class="fa-regular fa-circle"></i>
      <span>test task</span>
    </div>
    <!--./left-->

    <div class="right">
      <span class="edit-btn"
        ><i class="fa-solid fa-pen-to-square"></i>
        <span class="delete-btn"><i class="fa-solid fa-trash"></i></span>
      </span>
    </div>
    <!--./right-->
  </li>
</template>

<style scoped>
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
}

.right span i {
  color: #000;
}

.right span .delete-btn:hover {
  color: red;
}

.right span .edit-btn {
  color: dodgerblue;
}
</style>
