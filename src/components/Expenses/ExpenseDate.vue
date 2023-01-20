<script setup lang="ts">
import { reactive, toRefs } from "vue";

const props = defineProps<{
  date: Date;
}>();

const state = reactive<{
  month: string;
  day: string;
  year: number;
}>({
  month: props.date.toLocaleString("en-US", { month: "long" }),
  day: props.date.toLocaleString("en-US", { day: "2-digit" }),
  year: props.date.getFullYear(),
});

const { month, day, year } = toRefs(state);
</script>

<template>
  <div class="expense-date">
    <div class="expense-date__month">{{ month }}</div>
    <div class="expense-date__year">{{ year }}</div>
    <div class="expense-date__day">{{ day }}</div>
  </div>
</template>

<style lang="scss" scoped>
.expense-date {
  display: flex;
  flex-direction: column;
  width: 5.5rem;
  height: 5.5rem;
  border: 1px solid #ececec;
  background-color: #2a2a2a;
  color: white;
  border-radius: 12px;
  align-items: center;
  justify-content: center;

  &__month {
    font-size: 0.75rem;
    font-weight: bold;
  }

  &__year {
    font-size: 0.75rem;
  }

  &__day {
    font-size: 1.5rem;
    font-weight: bold;
  }
}
</style>
