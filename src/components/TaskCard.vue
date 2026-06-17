<template>
    <BaseCard>

        <template #task-card>
            <h3>{{ task.title }}</h3>
          </template>

        <template #status-badge>
           <p>Status: <strong :class="task.completed? 'completed':'pending'">{{ task.completed ? 'Completed' : 'Pending' }}</strong></p>
        </template>

        <template #buttons>
            <button @click="completeTask" :disabled="task.completed">Complete</button>
            <button @click="deleteTask">Delete</button>
        </template>

    </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

const props = defineProps({
    task: {
        type: Object,
        required: true
    }
})
const emit = defineEmits(['complete-task', 'delete-task'])
function completeTask() {
    emit('complete-task', props.task.id)
}
function deleteTask() {
    emit('delete-task', props.task.id)
}
</script>

<style scoped>
.completed{
    color: green;
}
.pending{
    color: orange;
}
button{
    padding: 4px 8px;
    border-radius: 4px;
    border: 1px solid #ccc;
}
</style>