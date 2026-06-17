<template>
  <BaseCard class="task-card">
    <div>
      <div class="task-card-header">
        <h1>{{ task.title }}</h1>
        <p v-if="task.completed" class="done">Done</p>
      </div>

      <div class="status">
        <p>Status:</p>
        <p :class="task.completed ? 'Completed' : 'Pending'">
          {{ task.completed ? "Completed" : "Pending" }}
        </p>
      </div>

      <div class="action">
        <button
          @click="$emit('complete', task.id)"
          :class="task.completed ? 'button-pending' : 'button-completed'"
        >
          {{ task.completed ? "Pending" : "Completed" }}
        </button>
        <button @click="$emit('delete', task.id)" class="delete">Delete</button>
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
    validate: (value) => {
      return "id" && "tittle" && "completed";
    },
  },
});

defineEmits(["complete", "delete"]);
</script>

<style scoped>
.task-card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.task-card-header .h1 {
  font-size: 20px;
  margin: 0;
}
.done {
  color: green;
  font-weight: bold;
}
.status {
  display: flex;
  gap: 10px;
  margin: 8px 0px;
}
.button-completed {
  color: green;
  font-weight: bold;
}
.button-pending {
  color: orange;
  font-weight: bold;
}
.delete {
  color: red;
  font-weight: bold;
}
.action {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}
button {
  padding: 4px 12px;
}
</style>
