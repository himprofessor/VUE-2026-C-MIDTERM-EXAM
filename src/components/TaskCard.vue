<template>
    <BaseCard>
        <div class="task-card">
            <h3>{{ task.title }}</h3>
            
            <span :class="['badge', task.completed ? 'completed-badge' : 'pending-badge']">
                {{ task.completed ? 'Completed' : 'Pending' }}
            </span>
            <div class="actions">
                <button 
                    class="complete-btn" 
                    @click="toggleComplete(task.id)">
                    {{ task.completed ? 'Complete' : 'Complete' }}
                </button>
                <button class="delete-btn" @click="deleteTask(task.id)">Delete</button>
            </div>
        </div>
    </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue'

defineProps({
    task: {
        type: Object,
        required: true
    }
})

const emit = defineEmits([
    'deleteTask',
    'toggle-complete'
])

const toggleComplete = (id) => {
    emit('toggle-complete', id)
}

const deleteTask = (id) => {
    emit('deleteTask', id)
}
</script>

<style scoped>
.task-card {
    text-align: center;
    padding: 10px;
}

.badge {
    display: inline-block;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 0.85rem;
    font-weight: bold;
    margin-top: 5px;
}

.actions {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 15px;
}

.complete-btn {
    color: rgb(24, 4, 4);
    border: none;
    padding: 8px 12px;
    cursor: pointer;
    border-radius: 4px;
}

.delete-btn {
    background: crimson;
    color: white;
    border: none;
    padding: 8px 12px;
    cursor: pointer;
    border-radius: 4px;
}
.pending-badge{
    color: rgb(236, 95, 8);
}
.completed-badge{
    color: rgb(6, 233, 6);
}
</style>
