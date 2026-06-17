<template>
    <div class="task-detail-card">
        <div v-if="task">
            <h2>Task Title: {{ task.title || 'No Task' }}</h2>


            <p v-if="task.completed === true"><strong>Status: </strong>Completed</p>
            <p v-else-if="task.completed !== null"><strong>Status: </strong>Pending</p>
            <p v-else>Enjoy Your day.</p>

            
            <span :class="['badge', { 'completed': task.completed === true, 'pending': task.completed === false }]">
                {{ task.completed === true ? 'Completed' : (task.completed === false ? 'Pending' : 'No Status') }}
            </span>

            
            <div v-if="task.completed !== null">
                <button @click="$emit('toggle-status', task.id)">
                    {{ task.completed ? 'Mark Pending' : 'Complete' }}
                </button>

                <button @click="$emit('delete-task', task.id)">Delete</button>
            </div>
            <div v-else>
                <button @click="$emit('delete-task', task.id)">Delete</button>
            </div>

        </div>

    </div>
</template>

<script setup>
defineProps({
    task: {
        type: Object,
        default: null
    }
});

defineEmits(['toggle-status', 'delete-task']);
</script>


<style lang="scss" scoped>
.student-detail-card {
    border: 2px solid #3498db;
    border-radius: 12px;
    padding: 24px;
    background-color: #fff;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    text-align: center;
    position: sticky;
    top: 20px;
}

h2 {
    margin: 0 0 6px 0;
    color: #2c3e50;
}
</style>