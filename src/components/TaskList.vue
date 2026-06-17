<template>
    <div class="list">
        <div v-if="items.length === 0" class="'no-data'">
            <p>No tasks left! Enjoy your time.</p>
        </div>

        <div v-else>
            <TaskCard
            v-for="x in items"
            :key="x.id"
            :task="x"
            @complete="$emit('do-complete', $event)"
            @remove="$emit('do-remove', $event)"/>
        </div>
    </div>
</template>


<!-- scriipt  -->
<script setup>
import TaskCard from './TaskCard.vue';
defineProps({
    items: Array
});

defineEmits(['do-complete', 'do-remove']);
</script>


<!-- style  -->
<style lang="scss" scoped>
.no-data {
    text-align: center;
    padding: 30px;
    background: white;
    border: 1px dashed #aaa;
}

</style>