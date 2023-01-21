<script setup lang="ts">
import { DUMMY_YEAR_OPTIONS } from "@/data";
import type { Item } from "@/models";

const years: Array<Item> = DUMMY_YEAR_OPTIONS;

const props = defineProps<{
  selected: string;
}>();

const emit = defineEmits<{
  (e: "filterChange", filteredYear: string): void;
}>();

function onFilterChange(event: Event) {
  emit("filterChange", (event.target as HTMLSelectElement).value);
}
</script>

<template>
  <div class="expenses-filter">
    <div class="expenses-filter__control">
      <label for="year">Filter By Year</label>
      <select
        id="year"
        :value="props.selected"
        @change="onFilterChange($event)"
      >
        <option v-for="(item, index) of years" :key="index" :value="item.value">
          {{ item.label }}
        </option>
      </select>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.expenses-filter {
  color: white;
  padding: 0 1rem;

  &__control {
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: space-between;
    margin: 1rem 0;
  }

  label {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  select {
    font: inherit;
    padding: 0.5rem 3rem;
    font-weight: bold;
    border-radius: 6px;
  }
}
</style>
