<script setup>
</script>

<template>
    <div class="wrapper">
        <slot></slot>
    </div>
</template>

<style scoped>
    .wrapper {
        position: relative;
    }
    .wrapper::before {
        --width: 8px;
        
        content: "";
        position: absolute;
        top: 0;
        bottom: 0;
        left: calc((var(--width) + var(--app-padding-x)) * -1);
        width: var(--width);
        background-color: #D9D9D9;
        border-radius: 10px;
    }
</style>
