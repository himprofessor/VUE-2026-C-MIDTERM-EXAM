<template>
    <div class="card">
        <slot></slot>

    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.card{
    background: white;
    padding: 16px;
    border-radius: 10px;
    box-shadow: 0 2px 10px gray;
    margin-bottom: 12px;

}
</style>