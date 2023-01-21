<script setup lang="ts">
import { reactive, toRefs } from "vue";

import Expenses from "@/components/Expenses/Expenses.vue";
import NewExpense from "@/components/NewExpense/NewExpense.vue";

import type { Expense } from "@/models";
import { DUMMY_EXPENSES } from "@/data";

const state = reactive<{ expenses: Array<Expense> }>({
  expenses: DUMMY_EXPENSES,
});

const { expenses } = toRefs(state);

function handleAddExpense(expense: Expense) {
  expenses.value.unshift(expense);
}
</script>

<template>
  <NewExpense @expenseAdd="handleAddExpense" />
  <Expenses :expenses="expenses" />
</template>

<style lang="scss" scoped></style>
