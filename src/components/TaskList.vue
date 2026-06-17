<script setup>
import TaskCard from './TaskCard.vue';

defineProps({
    tasks: {
        type: Array,
        required:true
    }

});

defineEmits (['toggle-complete', 'delete-task']);

</script>



<template>
<div class task-list>
    <p  v-if="Tasks.length == 0">No tasks yet. Add one</p>
    <Tasks-card
    v-for="Task in tasks"
    :key="task.id"
    :task="task"
    @toggle-complete="emit('toggle-complete',$event)"
    @delete-task="emit('delete-tasks',$event)"
/>
</div>
</template>