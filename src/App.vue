<template>
  <div>
    <h1>Task Management</h1>
    <div class="dashboard-layout">
      <div>
        <h3>All Task List</h3>
        <TaskList 
        :tasks="tasks" 
        @toggle-status="toggleTask($event)" 
        @delete-task="deleteTask($event)"
        @view-detail="handleTaskSelection($event)" />
      </div>
      <div class="card-column">
        <h3>Card of task detail</h3>
        <BaseCard 
        v-if="selectedTask" 
        :task="selectedTask" 
        @toggle-status="toggleTask(selectedTask.id)"
        @delete-task="deleteTask(selectedTask.id)" />
        <p v-else>Please select to view detail.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue';
import BaseCard from './components/BaseCard.vue';
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
  },
  {
    id: 5,
    title: "",
    completed: null
  }
]);

const selectedTask = ref(null)

const toggleTask = (id) => {
  const foundTask = tasks.value.find(item => item.id === id);
  if (foundTask) {
    foundTask.completed = !foundTask.completed;
  }
}
const deleteTask = (id) => {
  tasks.value = tasks.value.filter(item => item.id !== id)

  if (selectedTask.value && selectedTask.value.id === id) {
    selectedTask.value = null
  }
};
const handleTaskSelection = (task) => {
  selectedTask.value = task
}
</script>

<style lang="scss" scoped>
h1 {
  display: flex;
  justify-content: center;
}

.dashboard-layout {
  display: flex;
  justify-content: center;
}

.card-column {
  margin-left: 60px;
}
</style>