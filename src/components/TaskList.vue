<script setup>
import TaskCard from './TaskCard.vue';
const props = defineProps({
    tasks: {
        type: Array,
        required: true
    }
})
defineEmits(['complete-task', 'delete-task']);
</script>

<template>
    <div class="task-list">
        <div v-if="tasks.length === 0" class="task-list__empty">
            <p> No tasks left! Enjoy your free time.</p>
        </div>
        <div v-else class="task-list__grid">
            <TaskCard v-for="task in tasks" :key="task.id" :task="task"
                @completed-task="$emit('completed-task', $event)"
                @delete-task="$emit('delete-task', $event)">
            </TaskCard>
        </div>
    </div>
</template>