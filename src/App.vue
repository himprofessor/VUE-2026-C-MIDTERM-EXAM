<script setup>
import { ref } from "vue";
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

const selectedTask = ref(null)
function statusTask(task) {

  selectedTask.value = task

}
function deleteTask(id) {

  tasks.value =
    tasks.value.filter(
      task => task.id !== id
    )

}
 



</script>

<template>
  <div class="header">
    <h1>My Tasks</h1>
    <p>You 4 tasks today.</p>
  </div>
  <TaskList :tasks="tasks" @status-task="statusTask" @delete-task="deleteTask" />
</template>

<style scoped>
.header {
  text-align: center;

}
</style>
