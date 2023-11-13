<template>
  <div>
    <h1>Todo Project</h1>
    <h2>완료된 Todo : {{ store.doneTodosCount }}</h2>
    <TodoList />
    <TodoForm />
  </div>
</template>

<script setup>
import TodoList from "@/components/TodoList.vue";
import TodoForm from "@/components/TodoForm.vue";
import { useCounterStore } from "@/stores/counter";

const store = useCounterStore();
</script>

<style scoped></style>
