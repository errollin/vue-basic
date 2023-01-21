<script setup lang="ts">
import { Card } from "@/components/common";
import ExpenseList from "@/components/Expenses/ExpenseList.vue";
import ExpenseFilter from "@/components/Expenses/ExpenseFilter.vue";

import type { Expense } from "@/models";
import { reactive, toRefs, watchEffect } from "vue";

const props = defineProps<{
  expenses: Array<Expense>;
}>();

const state = reactive<{
  filteredYear: string;
  filteredExpenses: Array<Expense>;
}>({
  filteredYear: "2022",
  filteredExpenses: [],
});

const { filteredYear, filteredExpenses } = toRefs(state);

watchEffect(() => {
  filteredExpenses.value = props.expenses.filter((expense) => {
    return expense.date.getFullYear().toString() === filteredYear.value;
  });
});

function handleFilterChange(selectedYear: string) {
  filteredYear.value = selectedYear;
}
</script>

<template>
  <Card className="expenses">
    <ExpenseFilter
      :selected="filteredYear"
      @filterChange="handleFilterChange"
    />
    <ExpenseList :expenses="filteredExpenses" />
  </Card>
</template>

<style lang="scss" scoped>
.expenses {
  padding: 1rem;
  background-color: rgb(31, 31, 31);
  margin: 2rem auto;
  width: 50rem;
  max-width: 95%;
}
</style>
