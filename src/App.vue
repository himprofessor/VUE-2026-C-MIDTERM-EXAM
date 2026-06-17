<template>
  <div class="app">
    <div class="container">
      <div class="header">
        <div class="header-text">
          <h1>My Daily Tasks To Study</h1>
            <p>Build yourself to ready before start to real work industry</p>
          </div>
        </div>
        <div class="subtaitle">
        <span>Total task today: <strong>{{ totalTasks }}</strong> </span>
      </div>
        
      <div>
        <TaskList
        :tasks="tasks"
        @status="handleStatus"
        @delete="handleDelete"
        />
      </div>
    </div>
  </div>
</template>

<script setup>

import { ref , computed} from 'vue'
import TaskList from './components/TaskList.vue';

const tasks = ref([
  {
    id: 1,
    title: 'Finish Vue homework',
    completed: true
  },
  {
    id: 2,
    title: 'Practice CSS Flexbox layout',
    completed: true
  },

  {
    id: 3,
    title: 'Read industry readiness guide',
    completed: true
  }
])

const totalTasks = computed(() => tasks.value.length)

const handleStatus = (taskId) => {
  const targetTask = tasks.value.find(t => t.id === taskId);
  if (targetTask) {
    targetTask.completed = !targetTask.completed;
  }
};

const handleDelete = (taskId) => {
  tasks.value = tasks.value.filter(t => t.id !== taskId);
};

</script>

<style scoped>
  .app {
    min-width: 960px;
    margin: 0 auto;
    padding: 32px 20px 60px;
    background-color: rgb(238, 249, 255);
    border-radius: 20px;
  }

  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 24px;
  }

  .header-text h1 {
    margin: 0;
    font-size: 44px;
    font-weight: 700;
    color: rgb(41, 40, 40);
  }

  .header-text p {
    margin: 4px 0 0;
    font-size: 24px;
    color: gray;
  }

  .subtaitle {
    font-size: 24px;
    color: gray;
    text-align: right;
    padding: 30px;
    
  }

</style>