<template>
  <div class="task-card">
    <div class="task-header">
      <h3 :class="{ 'completed-title': task.completed }">{{ task.title }}</h3>
      <span v-if="task.completed" class="badge badge-done">[ Done ]</span>
    </div>
    <p class="status-text">
      Status: 
      <span :class="task.completed ? 'text-done' : 'text-pending'">
        {{ task.completed ? 'Completed' : 'Pending' }}
      </span>
    </p>
    
    <div class="task-actions">
      <button 
        v-if="!task.completed" 
        @click="$emit('complete-task', task.id)" 
        class="btn btn-complete"> Complete
      </button>
      <button 
        @click="$emit('delete-task', task.id)" 
        class="btn btn-delete">Delete
      </button>
    </div>

  </div>
</template>

<script setup>
const props = defineProps({
  task: {
    type: Object,
    required: true
  }
});

const emit = defineEmits([
  'complete-task', 
  'delete-task'
]);

</script>

<style scoped>

.task-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  margin: 0;
  font-size: 1.15rem;
  color: #1a202c;
}

.completed-title {
  text-decoration: line-through;
  color: #a0aec0;
}

.status-text {
  margin: 8px 0 16px 0;
  font-size: 0.9rem;
  color: #4a5568;
}

.text-pending { 
  color: #ff6d0c; 
  font-weight: bold; }
.text-done { 
  color: #09d066; 
  font-weight: bold; }
.badge {
  font-size: 0.85rem;
  font-weight: bold;
}

.badge-done { 
  color: #108a49; 
}
.task-actions {
  display: flex;
  justify-content: flex-end;
  gap: 8px;
}

.btn {
  padding: 6px 16px;
  border-radius: 4px;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  border: 1px solid transparent;
}

.btn-complete {
  background-color: #34b8ff;
  color: #2b6cb0;
  border-color: #bee3f8;
}

.btn-complete:hover { 
  background-color: #dee2e6; 
}
.btn-delete {
  background-color: #fff5f5;
  color: #ff0000;
  border-color: #fed7d7;
}

.btn-delete:hover { 
  background-color: #feb2b2; 
  }
</style>
