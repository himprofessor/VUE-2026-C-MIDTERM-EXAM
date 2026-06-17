
<script setup>
// import BaseCard from './BaseCard.vue';
const props = defineProps ({
    Task: Object,
});
const emit = defineEmits (['pending', 'completed'])
</script>
<template>
    <BaseCard> 
    <button @click="emit('pending',  Task)">Pending</button>
    <button @click="emit('completed',  Task)">Complete</button>
    </BaseCard>
</template>
<style scoped>
</style>