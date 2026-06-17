<template>
  <BaseCard
    :class="{ 'card-complete': task.completed, 'card-deleted': task.deleted }"
  >
    <template #header>
      <h3 class="task-title">{{ task.title }}</h3>
      <span :class="['status-badge', badgeClass]">
        {{ statusText }}
      </span>
    </template>

    <template #footer>
      <button
        v-if="!task.deleted"
        @click="$emit('complete-task', task.id)"
        class="btn-complete"
      >
        {{ task.completed ? "Pending" : "Complete" }}
      </button>
     <button class="delete-btn" @click="$emit('delete-task', task.id)">Delete</button>
    </template>
  </BaseCard>
</template>

<script setup>
import { computed } from "vue";
import BaseCard from "./BaseCard.vue";

const props = defineProps({
  task: {
    type: Object,
    required: true,
  },
});

defineEmits(["complete-task", "delete-task"]);

// show status text
const statusText = computed(() => {
  if (props.task.deleted) return "Deleted";
  return props.task.completed ? "Completed" : "Pending";
});

// status card
const badgeClass = computed(() => {
  if (props.task.deleted) return "badge-delete";
  return props.task.completed ? "badge-complete" : "badge-pending";
});

</script>

<style scoped>
.task-title {
  margin: 0;
  font-size: 1.1rem;
}
.done-label {
  color: #28a745;
  font-weight: bold;
  font-size: 0.9rem;
  margin: 4px 0 0 0;
}
.card-complete {
  border-color: #28a745;
  background-color: #f8fff9;
}
.card-deleted {
  opacity: 0.4;
  border-color: #dc3545;
  background-color: #fff8f8;
}
.card-deleted .task-title {
  text-decoration: line-through;
}

.status-badge {
  padding: 4px 10px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: bold;
}
.badge-pending {
  background-color: #fff3cd;
  color: #856404;
}
.badge-complete {
  background-color: #d4edda;
  color: #155724;
}
.badge-delete {
  background-color: #f8d7da;
  color: red;
}

button {
  padding: 6px 12px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  font-size: 0.85rem;
}
.btn-complete {
  background-color: #28a745;
  color: white;
}
.btn-delete {
  background-color: #dc3545;
  color: white;
}
button:hover {
  opacity: 0.9;
}  
</style>
