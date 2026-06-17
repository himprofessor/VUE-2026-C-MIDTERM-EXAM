<template>
  <div class="task-list">
    <div v-if="tasks.length === 0" class="empty-state">
      <h2>No tasks left!</h2>
      <p>Enjoy your free time.</p>
    </div>

    <div v-else>
      <BaseCard v-for="task in tasks" :key="task.id">
        <TaskCard 
          :task="task" 
          @complete-task="$emit('complete-task', $event)"
          @delete-task="$emit('delete-task', $event)"
        />
      </BaseCard>
    </div>
  </div>
</template>

<script setup>
import BaseCard from './BaseCard.vue';
import TaskCard from './TaskCard.vue';

const props= defineProps({
  tasks: {
    type: Array,
    required: true
  }
});

const emit= defineEmits([
  'complete-task', 
  'delete-task'
]);
</script>


<style scoped>

.empty-state {
  text-align: center;
  padding: 40px 20px;
  background-color: #ffffff;
  border: 2px dashed #cbd5e0;
  border-radius: 8px;
  color: #4a5568;
}
.empty-state h2 {
  margin: 0 0 8px 0;
  color: #1b6fff;
}
</style>
