<script setup>
import BaseCard from './BaseCard.vue';

const props = defineProps({
    task: {
        type: Object,
        required: true
    }
})

defineEmits(['completed-task', 'delete-task']);

</script>

<template>
    <BaseCard>
        <template #header>My Tasks</template>
        <div class="task-card">
            <div class="task-card-wrap">
                <span class="task-card__id">ID: {{ task.id }}</span>
            </div>
            <div class="task-card__info">
                <h3 class="task-card__title">{{ task.title }}</h3>
                <span :class="['label', task.completed ? 'label--success' : 'label--warning']">
                    {{ task.completed ? 'Completed' : 'Pending' }}
                </span>
            </div>
        </div>
        <template #footer>
            <div class="task-card__actions">
                <button class="btn btn--primary" @click="$emit('completed-task', task.id)">
                    Complete
                </button>
                <button class="btn btn--danger" @click="$emit('delete-task', task.id)">
                    Delete
                </button>
            </div>
        </template>
    </BaseCard>
</template>

<style scoped>
.label{
    padding: 4px 8px;
    font-size: 12px;
    font-weight: bold;
    border-radius: 4px;
    text-transform: uppercase;
}

.label--success{
    background: #d1e7dd;
    color: #0f5132;
}

.label--warning {
    background-color:red;
}

.task-card {
    display: flex;
    align-items: center;
    gap: 16px;

}
.task-card__title{
    font-size: 17px;
    font-weight: 700;
    color: #1a2744;
    margin: 0 0 4px;
}

.task-card-wrap {
    position: relative;
    flex-shrink: 0;
}

.task-card__actions {
    display: flex;
    gap: 8px;
}

.task-card__id {
    background: #1a2744;
    color: #fff;
    font-size: 9px;
    font-weight: 600;
    padding: 2px 6px;
    border-radius: 99px;
    white-space: nowrap;
    letter-spacing: 0.04em;
}

.btn {
    flex: 1;
    padding: 8px 14px;
    border: none;
    border-radius: 7px;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: opacity 0.15s, transform 0.1s;
    font-family: inherit;
}

.btn--primary {
    background: #1a2744;
    color: #fff;
}

.btn--danger {
    background: #fee2e2;
    color: #dc2626;
}
</style>
