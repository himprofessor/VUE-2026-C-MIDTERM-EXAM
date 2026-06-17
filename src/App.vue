<template>
  <div class="app-container">
    <header class="app-header">
      <h1>My Tasks</h1>
      <!-- Task Counter -->
      <span class="task-count">
        You have {{ activeCount }} {{ activeCount === 1 ? "task" : "tasks" }} today
      </span>
    </header>

    <TaskList
      :tasks="tasks"
      @toggle-complete="handleComplete"
      @toggle-delete="handleDeleteToggle"
    />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
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

const activeCount = computed(() => {
  return tasks.value.filter((t) => !t.completed && !t.deleted).length;
});

const handleComplete = (id) => {
  const selectedTask = tasks.value.find((t) => t.id === id);
  if (selectedTask) {
    selectedTask.deleted = !selectedTask.deleted;
  }
};
</script>

<style scoped>
.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 0 20px;
  font-family: Arial, sans-serif;
}
</style>
