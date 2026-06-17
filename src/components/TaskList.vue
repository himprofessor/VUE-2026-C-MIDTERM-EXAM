<template>
  <div class="task-list">
    <TaskCard
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @complete="$emit('complete', $event)"
      @delete="$emit('delete', $event)"
    />

    <p v-if="tasks.length === 0" class="empty">No task</p>
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

defineEmits(["complete", "delete"]);
</script>

<style scoped>
.empty {
  text-align: center;
  color: blue;
  padding: 24px;
}
</style>
