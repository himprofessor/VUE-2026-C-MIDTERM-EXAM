<template>
  <div class="app">
    <header class="app-header">
      <h1>My Task</h1>
      <p>You have {{ activeTask }} tasks today</p>
    </header>

    <main class="app-body">
      <TaskList
        :tasks="tasks"
        @complete="handleComplete"
        @delete="handleDelete"
      />
    </main>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";
import TaskList from "./components/TaskList.vue";

const tasks = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false,
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true,
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false,
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false,
  },
]);

const activeTask = computed(() => {
  return tasks.value.filter((task) => !task.completed).length;
});

const handleComplete = (id) => {
  const task = tasks.value.find((task) => task.id === id);
  if (task) task.completed = !task.completed;
};

const handleDelete = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id);
};
</script>

<style scoped>
.app {
  max-width: 400px;
  margin: 40px auto;
  font-family: sans-serif;
}
.app-header {
  margin-bottom: 20px;
}
</style>
