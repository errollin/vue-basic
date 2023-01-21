<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{
  label: string;
  value: number;
  maxValue: number;
}>();

const barFillHeight = computed<string>(() => {
  let barFillHeight = "0%";

  if (props.maxValue > 0) {
    barFillHeight = `${Math.round((props.value / props.maxValue) * 100)}%`;
  }

  return barFillHeight;
});
</script>

<template>
  <div class="chart-bar">
    <div class="chart-bar__inner">
      <div class="chart-bar__fill" :style="{ height: barFillHeight }"></div>
    </div>
    <div class="chart-bar__label">{{ props.label }}</div>
  </div>
</template>

<style lang="scss" scoped>
.chart-bar {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;

  &__inner {
    height: 100%;
    width: 100%;
    border: 1px solid #313131;
    border-radius: 12px;
    background-color: #c3b4f3;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }

  &__fill {
    background-color: #4826b9;
    width: 100%;
    transition: all 0.3s ease-out;
  }

  &__label {
    font-weight: bold;
    font-size: 0.5rem;
    text-align: center;
  }
}
</style>
