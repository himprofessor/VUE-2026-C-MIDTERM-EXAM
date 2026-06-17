<template>
  <div class="app">
    <header class="app-header">
      <div class="app-header__inner">
        <div>
          <p class="app-header__eyebrow">Task Tracker </p>
        </div>
        <div class="app-header__stats">
          <span class="stat-badge">You have {{ tasks.length }} tasks today </span>
        </div>
      </div>
    </header>

    <main class="app-main">
      <TaskList :tasks="tasks" @completed-task="TaskStatus" @delete-task="delteTask">

      </TaskList>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
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
])
function TaskStatus(id) {
  const targetTask = tasks.value.find(t => t.id === id)
  if (targetTask) {
    targetTask.completed = !targetTask.completed
  }

}

function delteTask(id) {
  tasks.value = tasks.value.filter(t => t.id !== id)
}
</script>
<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
  background-color: #f0f4f8;
  color: #1a2744;

}

.app {
  min-height: 100vh;
}

.app-header {
  background-color: #1a2744;
  padding: 0;
}

.app-header__inner {
  max-width: 960px;
  margin: 0 auto;
  padding: 28px 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.app-header__eyebrow {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: aquamarine;
  margin-bottom: 6px;
}

.app-header__stats {
  font-size: 28px;
  font-weight: 700;
  color: #ffffff;
  letter-spacing: -0.02em;
}

.stat-badge{
  background: rgba(45, 212, 191, 0.15);
  color: aquamarine;
  border: 1px solid rgba(45, 212, 191, 0.3);
  font-size: 13px;
  font-weight: 600;
  padding: 6px 14px;
  border-radius: 99px;
  letter-spacing: 0.03em;

}

.app-main {
  max-width: 960px;
  margin: 0 auto;
  padding: 32px 24px 60px;
  
}
</style>