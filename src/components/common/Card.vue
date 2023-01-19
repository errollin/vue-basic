<script setup lang="ts">
const props = defineProps<{
  className: string;
}>();
</script>

<template>
  <div :class="['card', `${props.className}`]">
    <slot></slot>
  </div>
</template>

<style lang="scss" scoped>
.card {
  border-radius: 12px;
  box-shadow: 0 1px 8px rgba(0, 0, 0, 0.25);
}
</style>
