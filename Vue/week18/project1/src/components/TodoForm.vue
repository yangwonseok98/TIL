<!-- TodoForm.vue -->
<template>
  <div>
    <form @submit.prevent="createTodo(todoText)" ref="formElem">
      <input type="text" v-model="todoText" />
      <input type="submit" />
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useCounterStore } from "@/stores/counter";
const todoText = ref("");

const formElem = ref(null);

const store = useCounterStore();
const createTodo = function (todoText) {
  store.addTodo(todoText);
  formElem.value.reset();
};
</script>

<style lang="scss" scoped></style>
