<template>
  <div class="base-card">

    <slot></slot>

  </div>
</template>

<style scoped>

.base-card {
  background-color: #dbf3f6;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
  box-shadow: 0 4px 6px -1px rgba(255, 85, 85, 0.1);
  padding: 20px;
  margin-bottom: 16px;
}

</style>
