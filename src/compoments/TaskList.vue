<template>
    <div class="task-list">
        <div class="header">
            <h1>My Tasks</h1>
            <p>You have {{ taskCount }} tasks today</p>
        </div>
        <div v-if="tasks.length === 0" class="status">
            <h2>No task left!</h2>
            <p>Enjoy your free time</p>
        </div>
        <div>
            <TaskCard v-for="task in tasks" :key="task.id" :task="task" @complete-task="completeTask"
                @delete-task="deleteTask" 
                @complet-task="completeTask"
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
    },
    taskCount: {
        type:Number,
        required: true
    }

})


const emit = defineEmits([
    'complete-task',
    'delete-task'
])

const completeTask = (taske) => {
    emit('complete-task', taske)
}

const deleteTask = (id) => {
    emit('delete-task', id)
}


</script>

<style scoped>
.header {
    background-color: #f4f4f4;
    padding: 20px;
    font-weight: bold;
    border-bottom: 2px solid #333;
    text-align: left;
    border-radius: 12px 12px 0 0;
}

.status{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 30px;
}

</style>