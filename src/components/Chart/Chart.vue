<script setup lang="ts">
import { computed } from "vue";

import ChartBar from "@/components/Chart/ChartBar.vue";

import type { Item } from "@/models";

const props = defineProps<{
  dataPoints: Array<Item>;
}>();

const totalMaximum = computed<number>(() => {
  return props.dataPoints
    .map((dataPoint) => {
      return +dataPoint.value;
    })
    .reduce((previousValue, currentValue) => {
      return previousValue + currentValue;
    }, 0);
});
</script>

<template>
  <div class="chart">
    <ChartBar
      v-for="dataPoint of props.dataPoints"
      :key="dataPoint.label"
      :label="dataPoint.label"
      :value="+dataPoint.value"
      :maxValue="totalMaximum"
    />
  </div>
</template>

<style lang="scss" scoped>
.chart {
  padding: 1rem 0;
  border-radius: 12px;
  background-color: #f8dfff;
  text-align: center;
  display: flex;
  justify-content: space-around;
  height: 10rem;
}
</style>
