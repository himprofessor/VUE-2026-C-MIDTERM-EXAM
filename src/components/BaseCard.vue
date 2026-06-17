<template>
  <div class="base-card">
    <header v-if="$slots.header" class="base-card-header">
      <slot name="header" />
    </header>
    <div>
      <slot />
      <slot name="body" />
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.base-card {
  padding: 16px;
  background-color: #fff;
  border: 2px solid gray;
  border-radius: 4px;
  margin-bottom: 10px;
}
.base-card-header {
  padding-bottom: 10px;
  margin-bottom: 10px;
}
</style>
