<script setup lang="ts">
import { Card } from "@/components/common";
import ExpenseDate from "@/components/Expenses/ExpenseDate.vue";

const props = defineProps<{
  title: string;
  amount: number;
  date: Date;
}>();
</script>

<template>
  <li>
    <Card className="expense-item">
      <ExpenseDate :date="props.date" />
      <div class="expense-item__description">
        <h2>{{ props.title }}</h2>
        <div class="expense-item__price">${{ props.amount }}</div>
      </div>
    </Card>
  </li>
</template>

<style lang="scss" scoped>
.expense-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  margin: 1rem 0;
  background-color: #4b4b4b;

  &__description {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: flex-end;
    flex-flow: column-reverse;
    justify-content: flex-start;
    flex: 1;

    & h2 {
      color: #3a3a3a;
      font-size: 1rem;
      flex: 1;
      margin: 0 1rem;
      color: white;
    }
  }

  &__price {
    font-size: 1rem;
    font-weight: bold;
    color: white;
    background-color: #40005d;
    border: 1px solid white;
    padding: 0.5rem;
    border-radius: 12px;
  }
}

@media (min-width: 580px) {
  .expense-item {
    &__description {
      flex-direction: row;
      align-items: center;
      justify-content: flex-start;
      flex: 1;
    }

    &__description h2 {
      font-size: 1.25rem;
    }

    &__price {
      font-size: 1.25rem;
      padding: 0.5rem 1.5rem;
    }
  }
}
</style>
