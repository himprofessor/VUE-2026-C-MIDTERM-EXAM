<template>
    <BaseCard>
        <p>{{ task.title }}</p>
        <p><strong>Status:</strong> {{ task.completed }}</p>
        <div class="btn-container">
            <button class="btn" @click="complete">Complete</button>
            <button @click="onDelete(task.id)">Delete</button>
        </div>
    </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
    task: Object
})

const emit = defineEmits(['delete-click']);

const onDelete = (id) => {
  emit('delete-click', id);
};

</script>

<style scoped>
.btn-container {
    display: flex;
    margin-left: 30vh;
}
.btn-container .btn {
    margin-right: 10px;
    background-color: rgb(13, 189, 13);
}
.btn-container button {
    background-color: red;
    padding: 7px 15px;
    border: none;
    border-radius: 5px;
    color: white;
}
</style>