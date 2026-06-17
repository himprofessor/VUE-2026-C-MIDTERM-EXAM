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
  }]);
const selectTask = ref(null);

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
  if (selectTask.value?.id === id) {
    selectTask.value = null;
  }
}

</script>

<template>
  <div class="container">
    <div class="form-card">
      <TaskList 
    :tasks="tasks" 
    @complete-task="completeTask" 
    @delete-task="deleteTask" />
    </div>

    



  </div>
</template>

<style scoped>

.container {

  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.form-card{
  background:#93268f22 ;
  width: 40vw;
  height: auto;
  display: flex;
  flex-direction: column;
  border-radius: 24px 24px  0 0;
  border: 1px solid black;
}
</style>
