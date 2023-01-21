<script setup lang="ts">
import { reactive, toRefs } from "vue";

import type { Expense } from "@/models";

const emit = defineEmits<{
  (e: "expenseDataSave", expense: Expense): void;
  (e: "expenseDataCancelSave"): void;
}>();

const state = reactive<{ title: string; amount: string; date: string }>({
  title: "",
  amount: "",
  date: "",
});

const { title, amount, date } = toRefs(state);

function onSubmit(event: Event) {
  event.preventDefault();

  const expenseData: Expense = {
    title: title.value,
    amount: +amount.value,
    date: new Date(date.value),
  };
  emit("expenseDataSave", expenseData);
}

function onCancel() {
  emit("expenseDataCancelSave");
}
</script>

<template>
  <form @submit="onSubmit($event)">
    <div class="new-expense__controls">
      <div class="new-expense__control">
        <label for="title">Title</label>
        <input id="title" type="text" v-model="title" required />
      </div>
      <div class="new-expense__control">
        <label for="amount">Amount</label>
        <input
          id="amount"
          type="number"
          min="0.01"
          step="0.01"
          v-model="amount"
        />
      </div>
      <div class="new-expense__control">
        <label for="date">Date</label>
        <input
          id="date"
          type="date"
          required
          min="2022-01-01"
          max="2023-12-31"
          v-model="date"
        />
      </div>
    </div>
    <div class="new-expense__actions">
      <button type="button" @click="onCancel">Cancel</button>
      <button type="submit">Add Expense</button>
    </div>
  </form>
</template>

<style lang="scss" scoped>
.new-expense__controls {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 1rem;
  text-align: left;

  .new-expense__control {
    label {
      font-weight: bold;
      margin-bottom: 0.5rem;
      display: block;
    }

    input {
      font: inherit;
      padding: 0.5rem;
      border-radius: 6px;
      border: 1px solid #ccc;
      width: 20rem;
      max-width: 100%;
    }
  }
}

.new-expense__actions {
  text-align: right;

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
