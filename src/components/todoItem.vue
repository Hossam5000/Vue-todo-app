<script setup>
</script>

<template>
  <li class="todoItem">

    <div class="left">
      <i class="fa-regular fa-circle"></i>
      <span>test task</span>
    </div><!--./left-->

    <div class="right">
      <span class="delete-btn"><i class="fa-solid fa-trash"></i></span>
    </div><!--./right-->
  </li>
</template>

<style scoped>
  li.todoItem{
    display: flex;
    justify-content: space-between;
    background-color: dodgerblue;
    color: #000;
  }
</style>