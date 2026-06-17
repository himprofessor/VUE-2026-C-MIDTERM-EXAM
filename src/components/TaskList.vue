<template>
  <div class="task-list">
    <!-- check task -->
    <div v-if="activeCount === 0" class="empty-state">
      <p>Hooray! No tasks remain. Enjoy your free time!</p>
    </div>
    <div v-else class="list-wrapper">
      <TaskCard
        v-for="item in tasks"
        :key="item.id"
        :task="item"
        @complete-task="$emit('toggle-complete', $event)"
        @delete-task="$emit('toggle-delete', $event)"
      />
    </div>
  </div>
</template>
<script setup>
import TaskCard from "./TaskCard.vue";
defineProps({
  tasks: {
    type: Array,
    required: true,
  },
});
//child events back up to App.vue
defineEmits(["toggle-complete", "toggle-delete"]);
</script>

<style scoped>
.list-wrapper {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.empty-state {
  text-align: center;
  padding: 40px 20px;
  background: #f9f9f9;
  border: 2px dashed #ccc;
  border-radius: 8px;
  color: #666;
  font-size: 1.1rem;
}
</style>
