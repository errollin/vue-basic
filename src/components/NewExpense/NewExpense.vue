<script setup lang="ts">
import { ref } from "vue";

import { Card } from "@/components/common";
import ExpenseForm from "@/components/NewExpense/ExpenseForm.vue";

import type { Expense } from "@/models";

const emit = defineEmits<{
  (e: "expenseAdd", expense: Expense): void;
}>();

const isEditing = ref<boolean>(false);

function handleSaveExpenseData(enteredExpenseData: Expense) {
  const expenseData: Expense = {
    ...enteredExpenseData,
    id: Math.random().toString(),
  };
  emit("expenseAdd", expenseData);
  handleStopEditing();
}

function handleStartEditing() {
  isEditing.value = true;
}

function handleStopEditing() {
  isEditing.value = false;
}
</script>

<template>
  <Card className="new-expense">
    <ExpenseForm
      v-if="isEditing"
      @expenseDataSave="handleSaveExpenseData"
      @expenseDataCancelSave="handleStopEditing"
    />
    <button v-else @click="handleStartEditing">Add New Expense</button>
  </Card>
</template>

<style lang="scss" scoped>
.new-expense {
  background-color: #a892ee;
  padding: 1rem;
  margin: 2rem auto;
  width: 50rem;
  max-width: 95%;
  text-align: center;

  button {
    font: inherit;
    cursor: pointer;
    padding: 1rem 2rem;
    border: 1px solid #40005d;
    background-color: #40005d;
    color: white;
    border-radius: 12px;
    margin-right: 1rem;

    &:hover,
    &:active {
      background-color: #510674;
      border-color: #510674;
    }

    &.alternative {
      color: #220131;
      border-color: transparent;
      background-color: transparent;

      &:hover,
      &:active {
        background-color: #ddb3f8;
      }
    }
  }
}
</style>
