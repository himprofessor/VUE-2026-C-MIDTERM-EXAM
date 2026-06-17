<template>
    <BaseCard>
        <div class="task-card">
            <h2>
                {{ task.title }}
            </h2>
            <div class="stutus-task">
                <span v-if="task.completeTask" class="badge status-completed">Completed</span>
                <span v-else class="badge status-pending">Panding</span>
            </div>
            <div class="actions">
                <button class="complete-btn" @click="completeTask(task)">
                    Complete
                </button>
                <button class="delete-btn" @click="deleteTask(task.id)">
                    Delete
                </button>
            </div>

        </div>
    </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
    task: {
        type: Object,
        riquired: true
    }
})

const emit = defineEmits([
    'complete-task',
    'delete-task'
])

const completeTask = (task) => {
    emit('complete-task', task)
}

const deleteTask = (id) => {
    emit('delete-task', id)
}

</script>

<style scoped>
.task-card {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.actions {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 10px;
}

.complete-btn {
    background: blue;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 8px 12px;
    cursor: pointer;
}

.delete-btn {
    background: red;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 8px 12px;
    cursor: pointer;
}

.badge {
    display: inline-block;
    padding: 4px 8px;
    font-size: 0.8rem;
    font-weight: bold;
    border-radius: 4px;
}

.status-pending {
    background-color: #ffeeba;
    color: #856404;
}

.status-completed {
    background-color: #d4edda;
    color: #155724;
}
</style>