<script setup lang="ts">
import ExpenseItem from "@/components/Expenses/ExpenseItem.vue";
import type { Expense } from "@/models";

const props = defineProps<{
  expenses: Array<Expense>;
}>();
</script>

<template>
  <div class="expenses-list">
    <ExpenseItem
      v-for="expense in props.expenses"
      :key="expense.id"
      :title="expense.title"
      :amount="expense.amount"
      :date="expense.date"
    />
  </div>
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
