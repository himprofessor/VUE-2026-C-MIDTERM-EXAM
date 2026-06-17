<template>
  <div class="task-card">
    <div class="task-content">
      <!-- Task Title & Done Badge -->
      <div class="task-header">
        <span :class="{ completed: task.completed }">{{ task.title }}</span>
        <span v-if="task.completed" class="done-badge">Done</span>
       
      </div>

      <!-- Status Badge -->
      <div class="task-status">
        Status: 
        <span :class="[, task.completed ? 'completed-dot' : 'pending-dot']"></span>
        {{ task.completed ? 'Completed' : 'Pending' }}
      </div>

      <!-- Buttons -->
      <div class="task-actions">
        <button @click="$emit('complete-task')" class="btn complete-btn" :disabled="task.completed">
          Complete
        </button>
        <button @click="$emit('delete-task')" class="btn delete-btn">
          Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TaskCard',
  props: {
    task: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
.task-card {
  background: e2e8f0;
  padding: 14px;
  margin-bottom: 16px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  border: 1px solid #e2e8f0;
}
.task-header {
  display: flex;
  justify-content: space-between;
  font-weight: bold;
  font-size: 1.1em;
  /* margin-bottom: 8px; */
}
.task-header span.completed {
  text-decoration: line-through;
  color: #718096;
}
.done-badge {
  background-color: #c6f6d5;
  color: #22543d;
  padding: 2px 8px;
  border-radius: 4px;
  font-size: 0.8em;
}
.task-status {
  font-size: 0.9em;
  color: #4a5568;
  margin-bottom: 16px;
}

.pending-dot { background-color: #dd6b20; }
.completed-dot { background-color: #319795; }
.task-actions {
  display: flex;
  justify-content: flex-end;
}
.btn {
  padding: 10px 16px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  font-weight: 500;
}
.complete-btn {
  background-color: #e2e8f0;
  color: #4a5568;
}
.complete-btn:hover:not(:disabled) {
  background-color: #cbd5e1;
}
.complete-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
.delete-btn {
  background-color: #daa9a9;
  color: #c53030;
}
.delete-btn:hover {
  background-color: #daa;
}
</style>
