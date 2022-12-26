<script setup>
    import TextAreaVue from './TextArea.vue';
</script>

<template>
    <div class="wrapper">
        <TextAreaVue placeholder="Имя" label-text="Имя" :is-required="true" />
        <TextAreaVue placeholder="Имя" label-text="Имя" :is-required="true" />
        <TextAreaVue placeholder="Имя" label-text="Имя" :is-required="true" />
        <TextAreaVue placeholder="Имя" label-text="Имя" :is-required="true" />
    </div>
</template>

<style scoped>
    .wrapper {
        display: flex;
        flex-direction: column;
        row-gap: 7px;
    }
</style>