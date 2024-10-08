<script setup>
  import { inject } from 'vue';

  import { C } from '@/common/C';
  import { Button, Layout } from '@/common/components';

  const { setDarkTheme, setLightTheme } = inject('themeProvider')
</script>

<template>
  <Layout>
    <Button text="Темная тема" :mode="C.BUTTON_MODS.PRIMARY_FIRST" :onClick="setDarkTheme" />
    <Button text="Светлая тема" :mode="C.BUTTON_MODS.PRIMARY_SECOND" :onClick="setLightTheme" />
  </Layout>
</template>

<style scoped>
</style>
