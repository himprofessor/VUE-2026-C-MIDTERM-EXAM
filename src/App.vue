<script setup>

import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
import TaskCard from './components/TaskCard.vue';

const tasks = [
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
];
const allTask = ref(null)

function handleComplete(task){
  task.complete =true
}
</script>

<template>
  <h1>My Task</h1>

  <TaskList :tasks="tasks" @complete="handleComplete" @delete="handleDelete"/>
  
</template>

<style scoped>

h1{
  text-align: center;
}
</style>
