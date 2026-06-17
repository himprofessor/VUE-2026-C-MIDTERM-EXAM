<script setup>
import TaskCard from './TaskCard.vue'

const props = defineProps({
    tasks: Array
})

defineEmits(['delete-task'])

</script>

<template>
    <div class="task-list">
        <TaskCard 
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @delete-task="(taskId) => $emit('delete-task', taskId)"
        >
        </TaskCard>
    </div>
    
</template>

<style scoped>
.task-list{
    display: flex;
    flex-direction: column;
    gap: 10px;
}
</style>