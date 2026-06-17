<template>
    <BaseCard>
        <div class="task-card">
            <div class="task-info">
                <h3 :class="{ 'completed-text': task.completed }">{{ task.title }}</h3>
                <span class="task-id">ID:{{ task.id }}</span>
                <span class="badge" :class="task.completed ? 'badge-completed' : 'badge-pending'">
                    {{ task.completed ? 'Completed' : 'Pending' }}
                </span>
            </div>

            <div class="task-actions">
                <button v-if="!task.completed" @click="completeTask" class="btn btn-complete">
                    Complete
                </button>

                <button @click="deleteTask" class="btn btn-delete">
                    Delete
                </button>
            </div>
        </div>
    </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

const props = defineProps({
  task: {
    type: Object,
    required: true
  }
});

const emit = defineEmits([
    'complete-task',
    'delete-task'
]);

const completeTask = () => {
    emit('complete-task', props.task.id)
}
const deleteTask = () => {
    emit('delete-task', props.task.id)
}

    
</script>

<style scoped>
.task-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
}
.task-id {
  font-size: 0.8rem;
  font-weight: bold;
  color: #93a0b3; 
  margin-right: 8px;
}
.completed-text {
  text-decoration: line-through;
  color: #a0aec0;
}
.task-info h3 {
  margin: 0 0 8px 0;
  font-size: 1.1rem;
  color: #1a202c;
}
.completed-text {
  text-decoration: line-through;
  color: #a0aec0;
}
.badge {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: bold;
}
.badge-pending { background-color: #feebc8; color: #c05621; }
.badge-completed { background-color: #c6f6d5; color: #22543d; }
.task-actions { display: flex; gap: 8px; }
.btn {
  padding: 8px 14px;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
}
.btn-complete { background-color: #3182ce; color: white; }
.btn-delete { background-color: #e53e3e; color: white; }
</style>