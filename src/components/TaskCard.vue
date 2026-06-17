<template>
    <base-card>
        <div class="task-row">
            <div>
                <h4 :class="{ done: task.completed}">{{ task.title }}</h4>
            </div>

            <span :class="['status', task.Completed ? 'is-done' : 'is-pending']">
                {{ task.completed ? 'completed' : 'Pending' }}
            </span>
        </div>

        <div class="actions">
            <button @click="$emit('complete', task.id)" :disabled="task.completed">Done</button>
            <button @click="$emit('remove', task.id)" class="btn-del">Delete</button>         
        </div>
    </base-card>
</template>


<!-- script  -->
<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
    task: {
        type: Object,
    }
});

defineEmits(['complete', 'remove']);
</script>


<!-- style  -->
<style lang="scss" scoped>
.task-row{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

h4 {
    margin: 0;
    font-size: 16px;
    color: #2c3e50;
    font-weight: 600;
}

.done {
    text-decoration: line-through;
    color: #95a5a6;
}

.status {
    padding: 4px 10px;
    font-size: 12px;
    font-weight: bold;
    border-radius: 20px;
    text-transform: capitalize;
    color: #856404;
}

.is-pending {
    background: #ffeaa7;
    color: #d63031;
}

.is-done {
    background:#ebf8ff;
    color: #2b6cb0;
}
.action{
    display: flex;
    gap: 10px;
}

button {
    margin-left: 5px;
    padding: 6px 14px;
    font-weight: 500;
    border: 1px solid #ccc;
    border-radius: 6px;
    background: #f8f9fa;
    color: #333;
    transition: all 0.2s ease;
    cursor: pointer;

    &:hover:not(:disabled) {
        background: #e2e6ea;
    }

    &:disabled {
        background: #eaeded;
        color: #bdc3c7;
        cursor: not-allowed;
    }

}

.btn-del {
    background: #ff7675;
    color: white;
    border: none;

    &:hover {
        background: #d63031;
    }
}

</style>