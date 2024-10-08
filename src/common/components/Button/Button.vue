<template>
  <button
    class="button"
    :class="mode"
    @click="onClick">
      {{ text }}
    </button>
</template>

<script setup>
  import { C } from '@/common/C';

  const props = defineProps({
    text: {
      type: String,
      required: true,
    },
    onClick: Function,
    mode: {
      validator: (v) => [
        C.BUTTON_MODS.PRIMARY_FIRST,
        C.BUTTON_MODS.PRIMARY_SECOND,
      ].indexOf(v) !== -1,
      default: () => C.BUTTON_MODS.PRIMARY_FIRST,
    }
  })

  const {
    mode,
    onClick,
    text
  } = props
</script>

<style scoped>
  .button {
    padding: 4px 8px;
    border-radius: 8px;
    font-size: 2rem;
  }

  .primary-first {
    background-color: var(--button-primary-first-background-color);
    color: var(--button-primary-first-text-color);
  }

  .primary-second {
    background-color: var(--button-primary-second-background-color);
    color: var(--button-primary-second-text-color)
  }
</style>