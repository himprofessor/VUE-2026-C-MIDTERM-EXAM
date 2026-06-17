
<script setup>
    // import TaskCard from '.components/TaskCard.vue'
defineProps({
  tasks: {
    type: Array,
    required: true
  }
});
defineEmits(['select-task']);
</script>
<template>
  <div class="task-list-container">
    <ul>
      <li v-for="task in tasks" :key="task.id" @click="$emit('select-task', task)":class="{ 'is-completed'
      :task.completed }">
        <span class="task-title">{{ task.title }}</span>
        <span class="badge">{{ task.completed ? 'Done' : 'Pending' }}</span>
      </li>
    </ul>
  </div>
</template>
<style scoped>
 ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid white;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}
.is-completed .task-title {
  text-decoration: line-through;
  color: gray;
}
.badge {
  font-size: 0.85em;
  padding: 2px 6px;
  border-radius: 3px;
  background-color:wheat;
}
</style>