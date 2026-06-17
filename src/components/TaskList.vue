<script setup>
    import TaskCard from './TaskCard.vue'

    defineProps({
        tasks :Array
    })
    defineEmits([
        'delete-task'
    ])

</script>

<template>
    <template v-if="tasks.length > 0">
        <div>
            <TaskCard
                v-for="task in tasks"
                :key="task.id"
                :task="task"
                @delete="$emit('delete-task', $event)" 
            />
            
                
        </div>
    </template>
        <div v-else class="empty-message">
            <h3> 🎉 No tasks left! </h3>
            <p>Enjoy your free time. </p>
        </div>

</template>



<style scoped>

</style>