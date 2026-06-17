<template>
    <div class="base-card">
        <div v-if="$slots.header" class="base-card__header">
            <slot name="header"></slot>

        </div>

        <div class="base-card__body">
            <slot> </slot>

        </div>

        <div v-if="$slots.footer" class="base-card__footer">
            <slot name="footer"> </slot>
        </div>
    </div>
</template>

<style scoped>
.base-card {
    background-color: #ffff;
    border-radius: 12px;
    border-left: 4px solid #2dd4df;
    box-shadow: 0 2px 12px rgba(26, 39, 68, 0.08);
    overflow: hidden;

}

.base-card__header {
    background: #f8f9fc;
    padding: 14px 20px;
    border-bottom: 1px solid #e8ecf4;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: #64748b
}

.base-card__body{
    padding: 20px;
}

.base-card__footer {
    padding: 14px 20px;
    border-top: 1px solid white;
    background-color: #f8f9fc;
}
</style>