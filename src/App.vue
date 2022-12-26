<script setup>
  import ContentWrapper from './components/ContentWrapper.vue';
  import MainUserInfoVue from './components/MainUserInfo.vue';
</script>

<template>
  <div class="container">
    <h1>Форма</h1>
    <form>
      <ContentWrapper>
        <MainUserInfoVue />
      </ContentWrapper>
    </form>
  </div>
</template>

<style scoped>
  .container {
    --app-padding-x: 20px;

    border-radius: 10px;
    padding: 10px var(--app-padding-x) 36px var(--app-padding-x);
    background-color: #fff;
  }
  .container > h1 {
    font: var(--default-font);
    text-align: center;
  }
  main {
    display: flex;
    flex-direction: column;
    row-gap: 13px;
  }
</style>
