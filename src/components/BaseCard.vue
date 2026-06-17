<template>
    <div class="card">
        <slot></slot>
    </div>
</template>
<style scoped>

.card{
    border: 1px solid rgb(158, 196, 214);
    border-radius: 4px;
    padding: 20px;
    margin: 10px;
    box-shadow: 0 2px 5px rgba(0,0,0,0,1);
}

</style>