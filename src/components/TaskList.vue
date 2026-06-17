<template>
  <div class="task-list">
    
    <div v-if="tasks.length === 0" class="empty-state">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#cbd5e0" stroke-width="2">
        <path d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
      </svg>
      <p>No tasks here. You're all caught up!</p>
    </div>

   
    <div v-else class="cards-container">
      <TaskCard
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @complete="$emit('complete', $event)"
        @delete="$emit('delete', $event)"
      />
    </div>
  </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';


defineProps({
  tasks: {
    type: Array,
    required: true
  }
});

defineEmits(['complete', 'delete']);
</script>

<style scoped>
.cards-container {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 48px 20px;
  background: #f8fafc;
  border-radius: 12px;
  border: 2px dashed #e2e8f0;
  color: #718096;
}
.empty-state p {
  margin-top: 12px;
  font-size: 1rem;
  font-weight: 500;
}
</style>
