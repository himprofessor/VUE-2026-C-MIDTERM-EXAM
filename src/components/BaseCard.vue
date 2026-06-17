<template>
    <div class="card">
        <slot></slot>
    </div>
</template>

<style scoped>
.card {
    border: solid 1.5px gray;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 10px;
    width: 60vh;
}
</style>