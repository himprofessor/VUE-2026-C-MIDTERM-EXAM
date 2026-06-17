<template>
    <div class="list">
        <TaskCard 
        v-for="task in tasks" 
        :key="task.id" 
        :id="task.id"
        :task="task"
        :completed="task.completed"
        @delete-click="passDeleteUp"
        />
    </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';

defineProps({
    tasks: Array,
});

const emit = defineEmits(['delete-task']);

const passDeleteUp = (id) => {
  emit('delete-task', id);
};

</script>