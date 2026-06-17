<template>
  <BaseCard>
    <div class="card-content">
        <h3 class="h3">
          {{ task.title }}
          <span v-if="task.completed" class="done">Done</span>
        </h3>
      
      <div v-if="!task.completed">
        <p >Status: {{ task.completed?'Complete':'Panding'}}</p>
        <div class="actions">
            <button class="complet"  @click="$emit('complete', task.id)">{{ task.completed?'Undo':'Done'}}</button>
            <button class="delete" @click="$emit('delete',task.id)">Delete</button>
        </div>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';


defineProps({
  task: {
    type: Object,
  }
});

defineEmits(['complete', 'delete']);
</script>



<style lang="scss" scoped>
.actions{
    display: flex;
    gap: 20px;
   
    .delete{
        background: red;
        border: none;
        border-radius: 3px;
        color: white;
        padding: 5px 10px;
    }
    .complet{
        background: green;
        border: none;
        border-radius: 3px;
        color: white;
           padding: 5px 10px;
    }
}
.h3{
    display: flex;
    justify-content: space-between;
}
.done{
    border: 1px solid red;
    border-radius: 2px;
    padding: 5px 10px;
    color: red;
}
</style>