<script setup>
import { ref } from 'vue';
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

const removeTask = (idToDelete) => {
  tasks.value = tasks.value.filter(task => task.id !== idToDelete);
};


</script>

<template>
  <h2>My Tasks you have 4 tasks today</h2>
  <div class="container">
    <TaskList 
    :tasks="tasks" 
    @delete-task="removeTask"
     />
  </div>
</template>