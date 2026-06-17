<script setup>
import BaseCard from'./BaseCard.vue';


definceProps({
    Task: {
        type: object,
        required: true
    }
});
const emit = defineEmits(['toggle-complete','delete-task']);
</script>
<template>
    <BaseCard>
        <div class="card-item">
            <input
            type="clickbox"
            :checked="task.completed"
            @change="emit('toggle-complete', task.id)">
            <span :class="{ completed: task.completed }">
        {{ task.text }}
      </span>
      <button @click="emit('delete-task', task.id)">Delete</button>
        </div>
    </BaseCard>
</template>

<style scope>
.task-team {
    display: flex;
    align-items: center;
    gap: 12px
}
.completed {
    text-decoration: line-through;
    color: #888;

}
.buttom{
    margin-left: auto;
    color:red;

}
</style>