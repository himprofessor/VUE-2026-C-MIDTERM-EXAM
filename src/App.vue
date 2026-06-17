<script setup>
import { ref, computed } from 'vue';
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

const currentFilter = ref('all');

const pendingTask = computed(() => {
  return tasks.value.filter(task => !task.completed).length;
});

const completedCount = computed(() => {
  return tasks.value.filter(task => task.completed).length;
});

const filteredTasks = computed(() => {
  if (currentFilter.value === 'pending') {
    return tasks.value.filter(task => !task.completed);
  }
  if (currentFilter.value === 'completed') {
    return tasks.value.filter(task => task.completed);
  }
  return tasks.value;
});

const completeTask = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) {
    task.completed = true;
  }
};

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
};

</script>

<template>
  <div id="app" class="container">

    <header class="header">
      <h1>Task Management Application</h1>
      <div class="counter-group">
        <span class="count-badge count-pending">
          {{ pendingTask }} Pending
        </span>
        <span class="count-badge count-completed">
          {{ completedCount }} Completed
        </span>
      </div> 

    </header>

    <div class="filter-toolbar">
      <button 
        @click="currentFilter = 'all'" 
        :class="{ active: currentFilter === 'all' }"
        class="filter-btn"
      >
        All ({{ tasks.length }})
      </button>

      <button 
        @click="currentFilter = 'pending'" 
        :class="{ active: currentFilter === 'pending' }"
        class="filter-btn"
      >
        Pending ({{ pendingCount }})
      </button>

      <button 
        @click="currentFilter = 'completed'" 
        :class="{ active: currentFilter === 'completed' }"
        class="filter-btn" >
        Completed ({{ completedCount }})
      </button>

    </div>
    <TaskList :tasks="filteredTasks" @complete-task="completeTask" @delete-task="deleteTask" />
  </div>
</template>

<style scoped>
body {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background-color: #edf2f7;
  margin: 0;
  padding: 40px 20px;
}
.container {
  max-width: 650px;
  margin: 0 auto;
  background: white;
  border-radius: 12px;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  padding: 24px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 2px solid #5f92c4;
  padding-bottom: 18px;
  margin-bottom: 34px;
}

.header h1 {
  margin: 0;
  font-size: 2rem;
  color: #04215b;
}

.count {
  margin: 0;
  color: #101112;
  font-weight: 500;
}

.filter-btn {
  flex: 1;
  padding: 8px 12px;
  border: none;
  background: transparent;
  color: #4a5568;
  font-weight: 600;
  font-size: 0.85rem;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.15s ease;
}
.filter-btn:hover {
  background-color: #edf2f7;
}

.filter-btn.active {
  background-color: #ffffff;
  color: #2b6cb0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
}
</style>
