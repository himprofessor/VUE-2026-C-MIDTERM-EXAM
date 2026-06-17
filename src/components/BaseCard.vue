<template>
    <div class="base-card">
        <slot></slot>
    </div>
</template>

<script setup>

</script>

<style scoped> 
    .base-card {
        background-color: rgb(237, 237, 237);
        padding: 34px;
        margin-bottom: 15px;
        box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
        border-left: 5px solid green;
        transition: all 0.5s;
        border-radius: 8px;
    }
</style>