<template>
    <div class="card">
        <slot></slot>
    </div>
</template>


<style lang="scss" scoped>
.card {
    background: #ffffff;
    border: 1px solid #ccc;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

</style>