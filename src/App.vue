<template>
  <div class="container">
    <h1>My Tasks</h1>
    <h2>You have 3 tasks today</h2>

    <TaskList
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-complete="toggleComplete"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
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

const toggleComplete = (taskId) => {
  const task = tasks.value.find((t) => t.id === taskId);
  if (task) {
    task.completed = !task.completed;
  }

};

const deleteTask = (taskId) => {
  tasks.value = tasks.value.filter((task) => task.id !== taskId);
};
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 20px auto;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

h1 {
  text-align: center;
}
</style>
