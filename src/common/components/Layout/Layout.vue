<template>
  <div class="layout">
    <slot></slot>
  </div>
</template>

<script setup>

</script>

<style scoped>
  .layout {
    display: flex;
    align-items: center;
    justify-content: space-around;
    background-color: var(--main-background-color);
    width: inherit;
    height: inherit;
  }
</style>