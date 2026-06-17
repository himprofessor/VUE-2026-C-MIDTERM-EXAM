<template>
  <BaseCard>
    <div class="task-content">
        <div class="task-info">
        <h3 :class="{ 'completed-text': task.completed }">
          {{ task.title }}
        </h3>
        <span
          class="badge"
          :class="task.completed ? 'badge-success' : 'badge-warning'"
        >
          {{ task.completed ? "Completed" : "Pending" }}
        </span>
      </div>

      <div class="task-actions">
        <button
          class="btn btn-action"
          :class="task.completed ? 'btn-undo' : 'btn-complete'"
          @click="$emit('complete', task.id)"
        >
          {{ task.completed ? "Undo" : "Complete" }}
        </button>
        <button class="btn btn-delete" @click="$emit('delete', task.id)">
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from "./BaseCard.vue";

defineProps({
  task: {
    type: Object,
    required: true,
  },
});

defineEmits(["complete", "delete"]);
</script>

<style scoped>
.task-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.task-info h3 {
  margin: 0 0 6px 0;
  font-size: 1.1rem;
  font-weight: 600;
  color: #1a202c;
  transition: color 0.3s;
}
.completed-text {
  text-decoration: line-through;
  color: #a0aec0 !important;
}
.badge {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
}
.badge-success {
  background-color: #c6f6d5;
  color: #22543d;
}
.badge-warning {
  background-color: #feebc8;
  color: #7b341e;
}
.task-actions {
  display: flex;
  gap: 8px;
}
.btn {
  padding: 8px 14px;
  border-radius: 6px;
  font-size: 0.875rem;
  font-weight: 500;
  cursor: pointer;
  border: none;
  transition: background-color 0.2s;
}
.btn-complete {
  background-color: #ebf8ff;
  color: #2b6cb0;
}
.btn-complete:hover {
  background-color: #bee3f8;
}
.btn-undo {
  background-color: #edf2f7;
  color: #4a5568;
}
.btn-undo:hover {
  background-color: #e2e8f0;
}
.btn-delete {
  background-color: #fed7d7;
  color: #9b2c2c;
}
.btn-delete:hover {
  background-color: #feb2b2;
}
</style>
