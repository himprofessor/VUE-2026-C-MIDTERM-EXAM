<template>
  <div class="task-card">
    <div class="student-content">
        <div class='status'>
            <BaseCard v-bind="props.completed">
              <template #BaseCard>
                <h3 style="color:green" v-if="props.completed" >Completed</h3>
                <h3 style="color:Orange " v-else >Pending</h3>
              </template>
            </BaseCard>
        </div>

      <h2 :style="{ textDecoration: props.completed ? 'line-through' : 'none', color: props.completed ? '#888' : 'black' }">{{ props.title }}</h2>
      <button 
  @click="$emit('toggleComplete', props.id)">
Complete
</button>

      <button style="background: red" @click="$emit('deleteTask', props.id)">
        Delete
      </button>
    </div>
  </div>
</template>

<script setup>
import BaseCard from "./BaseCard.vue";

const props = defineProps({
  id: Number,
  title: String,
  completed: Boolean,
});
</script>

<style scoped>
*{
    font-family: sans-serif;
}
.task-card {
  width: 280px;
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  position: relative;
  padding:12px;

}
.student-content{
    display: flex;
    flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
.status{
    position: absolute;
    top:0;
    right: 12px;
}

.student-image {
  width: 100%;
  height: 220px;
  object-fit: cover;
}

.student-content {
  padding: 16px;
}

strong {
  display: inline-block;
  margin: 10px 0;
  background: #f3f4f6;
  color: #2563eb;
  padding: 6px 12px;
  border-radius: 20px;
}

button {
  display: block;
  margin-top: 12px;
  padding: 8px 16px;
  border: none;
  border-radius: 8px;
  background: royalblue;
  color: white;
  cursor: pointer;
}
</style>
