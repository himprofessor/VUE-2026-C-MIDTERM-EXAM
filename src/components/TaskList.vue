<script setup>
import { defineProps, defineEmits } from 'vue';
import TaskCard from './TaskCard.vue';
const props = defineProps({
    tasks: Array
})
</script>

<template>
    <TaskCard v-for="task in tasks" :key="task.id" :tasks="task" @complete="$emit('complete', $event)" @delete="$emit('delete', $event)"/>

</template>