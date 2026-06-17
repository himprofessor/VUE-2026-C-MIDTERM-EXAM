<template>
    <div class="card">

        <div class="card-header">
            <slot name="task-card"></slot>
        </div>

        <div class="status-badge">
            <slot name="status-badge"></slot>
        </div>

        <div class="buttons">
            <slot name="buttons"></slot>
        </div>

    </div>

</template>

<script setup>

</script>

<style scoped>
.card {
    background: #f5f5f5;
    border: solid 1px #dec870;
    border-radius: 8px;
    padding: 16px;
    width: 100%;
    margin: 4px;
}


.buttons {
    display: flex;
    gap: 8px;
    margin-top: 12px;
}
</style>