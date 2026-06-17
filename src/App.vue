<template>
  <div class="header">
    <TaskList></TaskList>
    <p>Completed: {{ completedCount }}</p>
    <p>Pending: {{ pendingCount }}</p>
  </div>

  <div class="card" v-if="tasks.length > 0">
    <TaskCard
      v-for="task in tasks"
      :key="task.id"
      v-bind="task"
      @deleteTask="deleteCard"
      @toggleComplete="toggleComplete" 
    />
  </div>

  <div v-else>
    <h3>No tasks left!</h3>
  </div>

  <!-- <BaseCard v-for="task in tasks" v-bind="task" >
  </BaseCard> -->
</template>

<script setup>
import { computed, ref } from "vue";
import TaskList from "./components/TaskList.vue";
import TaskCard from "./components/TaskCard.vue";

function deleteCard(id) {
  tasks.value = tasks.value.filter((task) => task.id !== id);
}

const toggleComplete = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) {
    task.completed = !task.completed; 
  }
};

const tasks = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false,
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true,
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false,
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false,
  },
]);
const completedCount = computed(() => {
  return tasks.value.filter(task => task.completed).length;
});

const pendingCount = computed(() => {
  return tasks.value.filter(task => !task.completed).length;
});
</script>
<style lang="scss" scoped>
.card {
  display: flex;
  gap: 16px;
}
</style>
