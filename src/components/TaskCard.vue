<template>
  <div class="task-card interactive">
    <div class="task-info">
      <h3>Task Title: {{ task.title || 'No Specific Task' }}</h3>
      <button @click="$emit('select-task', task)" class="button">
        View Detail
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
    task: {
        type: Object,
        required: true
    }
})
defineEmits(['select-task'])
</script>

<style lang="scss" scoped>
.task-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  display: flex;
  gap: 16px;
  align-items: center;
  background-color: #fff;
  transition: all 0.2s ease;
  }
  .task-info {
    h3 { margin: 0 0 8px 0; color: #333; }
    p { margin: 4px 0; color: #666; }
  }
  .button{
    padding: 4px;
    border-radius: 4px;
    background-color: #3498db;
    color: white;
}
</style>