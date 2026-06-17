<template>
    <div class="card">
        <slot></slot>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.card {
border: 1px solid #ddd;
border-radius: 10px;
padding: 16px;
margin: 10px;
box-shadow: 0 2px 5px rgba(0,0,0,0.2);
background: white;
}
</style>