<template>
  <div>
      
    <TaskList
    :tasks="tasks"
    :total-tasks="tasks.length"
    @complete="completeTask"
    @delete="deleteTask"
    />

  </div>
</template>

<script setup>
import TaskList from './components/TaskList.vue';
import { ref } from 'vue';
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
const completeTask=(id)=>{
  const task = tasks.value.find(t=>t.id===id);
  if(task) task.completed=!task.completed;

}
const deleteTask=(id)=>{
  tasks.value =tasks.value.filter(t=>t.id !==id );
}
</script>

<style lang="scss" scoped>

</style>