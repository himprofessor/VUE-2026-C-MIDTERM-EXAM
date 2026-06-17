<template>
  <TaskList :tasks="tasks" @complete-task="completeTask" @delete-task="deleteTask"></TaskList>

</template>
<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
function completeTask(id) {
  const task = tasks.value.find(task => task.id === id)
  if (task) {
    task.completed = true
  }
}
function deleteTask(id) {
  tasks.value = tasks.value.filter(task => task.id !== id)
}
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
</script>

<style scoped></style>
