<script setup lang="ts">
import Expenses from "@/components/Expenses/Expenses.vue";

import type { Expense } from "@/models";
import { DUMMY_EXPENSES } from "@/data";

const expenses: Array<Expense> = DUMMY_EXPENSES;
</script>

<template>
  <Expenses :expenses="expenses" />
</template>

<style lang="scss" scoped></style>
