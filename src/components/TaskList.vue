<template>
    <div class="task-list">
        <div v-if="tasks.length === 0" class="empty-state">
             🎉 All tasks completed! You're all caught up.
        </div>

        <div v-else class="list-container">
            <TaskCard 
                v-for="task in tasks" 
                :key="task.id" 
                :task="task" 
                @complete-task="completeTask" 
                @delete-task="deleteTask" 
            />
        </div>
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

const emit = defineEmits([
  'complete-task',
  'delete-task'
]);

const completeTask = (id) => {
  emit('complete-task', id);
};

const deleteTask = (id) => {
  emit('delete-task', id);
};

</script>

<style scoped>
.list-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.empty-state {
  text-align: center;
  padding: 40px;
  color: #718096;
  background: #f7fafc;
  border: 2px dashed #e2e8f0;
  border-radius: 10px;
  font-size: 1.1rem;
}
</style>