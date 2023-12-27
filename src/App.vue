<script setup>
import { reactive, computed } from "vue";
import TodoList from "./components/TodoList.vue";
import CompletedTodo from "./components/CompletedTodo.vue";
import TitleTodo from "./components/TitleTodo.vue";

const state = reactive({
  items: [],
});

const addTodo = (name) => {
  state.items.push({
    id: state.items.length + 1,
    name: name,
    completed: false,
    deleted: false,
  });
};

const noDone = computed(() => {
  return state.items.filter((item) => !item.completed && !item.deleted);
});

const uncompleted = computed(() => {
  return state.items.filter((item) => item.completed && !item.deleted);
});

</script>

<template>
  <TitleTodo @add-todo="addTodo" /> 
  <div class="cards">
    <TodoList :shipment="noDone" />
    <CompletedTodo :middleman="uncompleted" />
  </div>
</template>

