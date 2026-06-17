<template>
    <div class="task-list">
        <div>
            <h1>My Tasks</h1>
            <p>You have {{ tasks.length }} tasks today</p>
        </div>
        <div v-if="tasks.length > 0">
            <TaskCard v-for="task in tasks" :key="task.id" :task="task" @complete-task="$emit('complete-task', $event)"
                @delete-task="$emit('delete-task', $event)"></TaskCard>
        </div>
        <div v-else>
            <h3>🎉 No tasks left!</h3>
            <p>Enjoy your free time.</p>
        </div>
    </div>
</template>
<script setup>
import TaskCard from './TaskCard.vue';
defineProps({
    tasks: Array
})

defineEmits([
    'complete-task',
    'delete-task'
])
</script>
<style scoped>
.task-list {
    width: 80%;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>