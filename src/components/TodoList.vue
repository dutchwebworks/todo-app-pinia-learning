<script setup>
  import { useTodoListStore } from "../stores/todoList";
  import { storeToRefs } from "pinia";

  const store = useTodoListStore();
  const { todoList } = storeToRefs(store);
  const { toggleCompleted, deleteTodo } = store;
</script>

<template>
  <ul>
    <li v-for="todo in todoList" :key="todo.id">
      <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
      <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
      <span @click.stop="deleteTodo(todo.id)">&#10060;</span>
    </li>
  </ul>
</template>

<style scoped>
  .completed {
    text-decoration: line-through;
  }
</style>