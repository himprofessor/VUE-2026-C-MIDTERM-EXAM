<template>
  <div class="task-list">
    <TaskCard 
      v-for="item in tasks" 
      :key="item.id" 
      :task="item" 
      @toggle-status="$emit('toggle-task', item.id)"
      @delete-task="$emit('delete-task', item.id)"
      @select-task="$emit('view-detail', item)" 
    />
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

defineEmits(['toggle-task', 'delete-task', 'view-detail']);
</script>


<style lang="scss" scoped>
.task-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 16px;
}
</style>