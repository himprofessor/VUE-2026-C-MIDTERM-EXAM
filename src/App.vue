<script setup>

import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
const tasks = ref ([
  { id: 1, title: "Finish Vue homework", completed: false},
  { id: 2, title: "Buy groceries", completed: true },
  { id: 3, title: "Call the dentist", completed: false },
  { id: 4, title: "Read one chapter of a book", completed: false },
]);
const selectedTask  =  ref(null)
function handleSelectTask(task) {
  selectedTask.value = task;
}
</script>

<template>
    <h1 style="border: 2px;">My Task Management App </h1>
    <TaskList :tasks="tasks" @select-task="handleSelectTask"/>
    <div v-if="selectedTask" class="task-details">
    <h2>Selected Task Details</h2>
    <p><strong>ID:</strong> {{ selectedTask.id }}</p>
    <p><strong>Title:</strong> {{ selectedTask.title }}</p>
    <p><strong>Status:</strong> {{ selectedTask.completed ? 'Completed' : 'Pending' }}</p>
    <button @click="selectedTask = null">Clear Selection</button>
  </div>
</template>

<style scoped>
.task-details{
  margin-top: 20px;
  padding: 15px;
  border:1px solid gray ;
  border-radius: 4px;
}
</style>
