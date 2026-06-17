<script setup>
import { ref, watch } from 'vue';
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
const completed_task = (task) => {
  tasks.value.forEach(item => {
    if(item.id == task.id){
      item.completed = true
    }
  })
}
const deleted_task = (task) => {
  tasks.value = tasks.value.filter(record => record.id !== task.id);
}
let number_task = tasks.value.length
watch(tasks, () => {
   number_task = tasks.value.length
})

</script>

<template>
  <div class="container">
    <h1>Task Management</h1>
    <div>
      Tasks: {{ number_task }}
    </div>
    <TaskList
      :tasks="tasks"
      @completed_task="completed_task"
      @deleted_task="deleted_task"
     />
  </div>
</template>

<style scoped>
.container {
max-width: 1200px;
margin: auto;
padding: 20px;
}
</style>
