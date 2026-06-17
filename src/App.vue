<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue';


const task = ref([
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

const selectedTask = ref(task) 

function handlesComplete(task){
  selectedTask.value = task
}
function deleteTask(id){
  task.value = task.value.filter(t =>t.id !==id)
}


</script>

<template>
  <h1>My tasks</h1>
  
  <TaskList
    
    :tasks = "task"
    @complete-task="handlesComplete"
    @delete-task="deleteTask"
    
  />
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 15px;
  padding: 10px;
}
</style>




