<template>
  <div class="app-layout">
    <header class="app-header">
      <h1>My Tasks</h1>
      <p v-if="tasks.length > 0">I have {{ pendingCount }} tasks today</p>
    </header>

    <main class="app-main">
      <TaskList 
        :tasks="tasks" 
        @complete-task="handleCompleteTask"
        @delete-task="handleDeleteTask"
      />
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  }
]);
const pendingCount = computed(() => {
  return tasks.value.filter(task => task.completed).length;
});

const handleCompleteTask = (id) => {
  const targetTask = tasks.value.find(task => task.id === id);
  if (targetTask) {
    targetTask.completed = true;
  }
};

const handleDeleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
};
</script>


<style>

body {
  font-family: Arial, sans-serif;
  background-color: #a6d1ee;
  color: #546075;
  margin: 0;
  padding: 40px 20px;
}

.app-layout {
  max-width: 500px;
  margin: 0 auto;
  background-color: #78b1eb;
  border: 2px solid #c8ddf4;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05);
}

.app-header {
  background-color: #ffffff;
  padding: 24px;
  border-bottom: 2px solid #247fdf;
}

.app-header h1 {
  margin: 0;
  font-size: 1.5rem;
}

.app-header p {
  margin: 4px 0 0 0;
  color: #46505f;
}

.app-main {
  padding: 20px;
}
</style>
