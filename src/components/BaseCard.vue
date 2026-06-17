<template>
    <div class="base-card">
        <slot></slot>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.base-card{
    background:#fff;
    border-radius: 12px;
    padding: 18px;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03);
    border: 1px solid #e2e8f0;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.base-card:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}
</style>