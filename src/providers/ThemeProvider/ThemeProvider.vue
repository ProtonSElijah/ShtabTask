<template>
  <slot></slot>
</template>

<script setup>
  import { onMounted, provide, ref, watch } from 'vue';

  import { C } from '@/common/C';

  const getStartTheme = () => {
    return localStorage.getItem("user-theme")
      ?? window.matchMedia("(prefers-color-scheme: dark)").matches
        ? C.THEMES.DARK : C.THEMES.LIGHT
  }

  const __theme = ref(getStartTheme())

  const setLightTheme = () => {
    __theme.value = C.THEMES.LIGHT
  }

  const setDarkTheme = () => {
    __theme.value = C.THEMES.DARK
  }

  onMounted(() => {
    let htmlElement = document.documentElement;
    htmlElement.setAttribute('theme', __theme.value);
  })

  watch(__theme, () => {
    let htmlElement = document.documentElement;
    htmlElement.setAttribute('theme', __theme.value);

    localStorage.setItem("user-theme", __theme.value)
  })

  provide('themeProvider', {
    setDarkTheme,
    setLightTheme,
  })
</script>