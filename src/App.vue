<script setup>
  import ContentWrapper from './components/ContentWrapper.vue';
</script>

<template>
  <div class="wrapper">
    <header>
      <h1>Форма</h1>
    </header>
    <main>
      <ContentWrapper />
    </main>
  </div>
</template>

<style scoped>
  .wrapper {
    --app-padding-x: 20px;
    
    max-width: 570px;
    border-radius: 10px;
    padding: 10px var(--app-padding-x) 36px var(--app-padding-x);
    background-color: #fff;
  }
  header {
    text-align: center;
  }
  h1 {
    font: var(--default-font);
  }
</style>
