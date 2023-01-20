<script setup lang="ts">
import { Card } from "@/components/common";
import ExpenseList from "@/components/Expenses/ExpenseList.vue";

import type { Expense } from "@/models";

const props = defineProps<{
  expenses: Array<Expense>;
}>();
</script>

<template>
  <Card className="expenses">
    <ExpenseList :expenses="props.expenses" />
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
