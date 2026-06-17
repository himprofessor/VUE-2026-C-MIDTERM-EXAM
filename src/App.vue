<script setup>
import { ref } from 'vue'
import TaskCard from './components/TaskCard.vue'
import TaskList from './components/TaskList.vue'

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
]

function deleteTask(taskId){
  tasks.value = tasks.vlue.filter(task => task.id !== taskId)
}
</script>

<template>
  <div class="header">
    <h1>My Tasks</h1>
  <p>You have {{ tasks.length }} task{{ tasks.length === 1 ? '' : 's' }} today</p>

  <TaskList 
  :tasks="tasks"
  @delete-task="deleteTask">
  </TaskList>
  </div>

</template>


<style scoped>
p{
  font-size: 16px;
}
.header{
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 15px;
}
</style>