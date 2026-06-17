<script setup>
import BaseCard from './BaseCard.vue'

const props = defineProps({
    task: {
        type: Object,
        required: true
    }
})
const emit = defineEmits(['delete-task'])

function handleDelete() {
  emit('delete-task', props.task.id)
}

</script>

<template>
    <BaseCard>
        <p>{{ task.title }}</p>
        <p>Status: {{ task.completed ? 'completed': 'Pending'}}</p>

        <div class="button">
            <button>Complete</button>
            <button @click="handleDelete">Delete</button>
        </div>
    </BaseCard>
</template>

<style scoped>
p{
    font-size: 20px;
}
.button{
    display: flex;
    gap: 16px;
}
</style>