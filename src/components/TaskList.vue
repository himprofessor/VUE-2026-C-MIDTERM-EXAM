<template>
    <div class="task-list">
        <div v-if="tasks.length === 0" class="empty">
            <p> All caught up! No tasks left for today. please ejoy your life</p>
        </div>

        <div v-else>
            <TaskCard
            v-for="item in tasks"
            :key="item.id"
            :task="item"
            @status="$emit('status', $event)"
            @delete="$emit('delete', $event)"
            />

        </div>

    </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';

    defineProps({
        tasks:  {
            type: Array,
            required: true
        }
    });

    defineEmits(['status', 'delete']);

</script>

<style>

    .empty {
        text-align: center;
        padding: 2rem;
        background: #f2f2f2;
        border-radius: 8px;
        color: #666;
    }

</style>