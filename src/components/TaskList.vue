<template>
  <div class="task-card">
    <span>{{ task.title }}</span>
    <span v-if="task.completed"> (Completed)</span>
    

    <button @click="completeTask">Complete</button>
    <button @click="deleteTask">Delete</button>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  methods: {
    completeTask() {
    
      this.$emit('complete-task');
    },
    deleteTask() {
      this.$emit('delete-task');
    }
  }
}
</script>

<style scoped>
.task-card {
  display: grid;
  grid-template-columns: repeat(4, minmax(250px, 1fr));
  gap: 20px;
};
</style>

