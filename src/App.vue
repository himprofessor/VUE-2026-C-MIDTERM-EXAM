<script setup>
import { ref, watch, onMounted } from 'vue';
import TaskList from './components/TaskList.vue';
const newTask = ref('');
const tasks = ref([]);
onMounted(() => {
  tasks.value = JSON.parse(localStorage.getItem('my-tasks') || '[]');
});
watch(tasks, (newTasks) => {
  localStorage.setItem('my-tasks', JSON.stringify(newTasks));
}, { deep: true });
const addTask = () => {
  if (!newTask.value.trim()) return;
  tasks.value.push({
    id: Date.now(),
    text: newTask.value,
    completed: false
  });
  newTask.value = '';
};

const handleToggleComplete = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) task.completed = !task.completed;
};

const handleDeleteTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
};
</script>

<template>
  <div class="app-container">
    <h1>Task Manager</h1>
    
    <div class="input-group">
      <input v-model="newTask" @keyup.enter="addTask" placeholder="What needs to be done?">
      <button @click="addTask">Add Task</button>
    </div>
    <TaskList 
      :tasks="tasks" 
      @toggle-complete="handleToggleComplete"
      @delete-task="handleDeleteTask"
    />
  </div>
</template>

<style>
.app-container {
  max-width: 500px;
  margin: 40px auto;
  font-family: sans-serif;
  padding: 0 20px;
}
.input-group {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
}
input[type="text"] {
  flex: 1;
  padding: 8px;
}
</style>
<script setup>
import { ref, watch, onMounted } from 'vue';

const newTask = ref('');
const tasks = ref([]);

onMounted(() => {
  tasks.value = JSON.parse(localStorage.getItem('my-tasks') || '[]');
});
watch(tasks, (val) => {
  localStorage.setItem('my-tasks', JSON.stringify(val));
}, { deep: true });
const addTask = () => {
  if (newTask.value.trim() === '') return;
  tasks.value.push({ id: Date.now(), text: newTask.value, completed: false });
  newTask.value = '';
};

const removeTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
};
</script>

<template>
  <div class="task-manager">
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task">
    <button @click="addTask">Add</button>

    <ul>
      <li v-for="task in tasks" :key="task.id">
        <input type="checkbox" v-model="task.completed">
        <span :style="{ textDecoration: task.completed ? 'line-through' : '' }">
          {{ task.text }}
        </span>
        <button @click="removeTask(task.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>
