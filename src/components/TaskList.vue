<template>
  <div class="task-list">
    <BaseCard>
      <h1>📋 My Tasks</h1>

        <div v-if="tasks.length>0">
            <p>You have {{ tasks.length }} tasks today</p>
            <div v-for="task in tasks" :key="task.id">
            <TaskCard
                :task ="task"
                @complete="$emit('complete',$event)"
                @delete="$emit('delete',$event)"


            />
            </div>

        </div>
        <div v-else >
            <h2>No tasks left!</h2>
            <p>Enjoy your free time.</p>

        </div>

    </BaseCard>

  </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';
import BaseCard from './BaseCard.vue';


defineProps({
  tasks: {
    tasks:{
        type:Array,
        required:true
    },
    totalTasks:{
        type:Number,
        required:true

    }
  }
});

defineEmits(['complete', 'delete']);
</script>

<style lang="scss" scoped>

</style>