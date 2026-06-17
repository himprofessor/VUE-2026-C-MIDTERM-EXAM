<template>
  <div v-if="tasks.length > 0" class="task-grid">
    <TaskCard
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @delete-task="deleteTask"
      @toggle-complete="Complete"
    />
  </div>

  <div v-else class="empty-state">
    <p>No tasks left! Enjoy your free time.</p>
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

const emit = defineEmits(["deleteTask", "toggle-complete", "empty-state"]);

const deleteTask = (id) => {
  emit("deleteTask", id);
};

const Complete = (id) => {
  emit("toggle-complete", id);
};
const state = (id) => {
  emit("empty-state", id);
};
</script>

<style scoped>
.task-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(250px, 2fr));
  gap: 20px;
}
.empty-state {
  text-align: center;
  padding: 40px;
  font-size: 1.2rem;
  color: #666;
}
</style>
