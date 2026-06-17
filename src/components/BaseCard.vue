<!-- src/components/BaseCard.vue -->
<template>
  <div class="base-card">
    <!-- Slot for dynamic content -->
    <slot></slot>
  </div>
</template>

<style scoped>
.base-card {
   display: grid;
    grid-template-columns: repeat(4, minmax(250px, 1fr));
    gap: 20px;
    margin-top: 20px;
}
</style>
