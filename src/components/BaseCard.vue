<template>
    <div class="task">
        <slot></slot>
    </div>
</template>

<style scoped>
.task {
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 16px;
    padding: 20px;
    margin: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    transition: 0.2s ease;
    }
.task:hover {
    transform: translateY(-4px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}
</style>


