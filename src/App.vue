<template>
  <div class="app-container">
    <header class="app-header">
      <h1>My Task Manager</h1>
    </header>
    <main class="main-content">
      <TaskList 
        :tasks="tasks" 
        @complete="toggleComplete" 
        @delete="deleteTask" 
      />
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue'; 


const tasks = ref([
  { id: 1, title: "Finish Vue homework", completed: false },
  { id: 2, title: "Buy groceries", completed: true},
  { id: 3, title: "Call the dentist", completed: false },
  { id: 3, title: "Read one chapter of a book", completed: false }
]);


const toggleComplete = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) {
    task.completed = !task.completed;
  }
};


const deleteTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}
body {
  background-color: #f1f5f9;
  margin: 0;
  padding: 0;
}
.app-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 0 20px;
}
.app-header {
  text-align: center;
  margin-bottom: 30px;
}
.app-header h1 {
  color: #1e293b;
  margin: 0 0 8px 0;
}
.app-header p {
  color: #64748b;
  margin: 0;
}
</style>
