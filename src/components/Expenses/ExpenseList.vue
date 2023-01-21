<script setup lang="ts">
import ExpenseItem from "@/components/Expenses/ExpenseItem.vue";
import type { Expense } from "@/models";

const props = defineProps<{
  expenses: Array<Expense>;
}>();
</script>

<template>
  <ul v-if="props.expenses.length > 0" class="expenses-list">
    <ExpenseItem
      v-for="expense in props.expenses"
      :key="expense.id"
      :title="expense.title"
      :amount="expense.amount"
      :date="expense.date"
    />
  </ul>
  <h2 v-else class="expenses-list__fallback">No Expenses Found!</h2>
</template>

<style lang="scss" scoped>
.expenses-list {
  list-style: none;
  padding: 0;

  &__fallback {
    color: white;
    text-align: center;
  }
}
</style>
