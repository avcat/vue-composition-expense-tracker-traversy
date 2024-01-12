<script setup>
import MainHeader from './components/MainHeader.vue';
import MainBalance from './components/MainBalance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import TransactionAdd from './components/TransactionAdd.vue';

import { ref, computed } from 'vue';

const transactions = ref([
  { 
    id: 1,
    text: 'Flowers',
    amount: -20
  },
  {
    id: 2,
    text: 'Book',
    amount: -20
  },
  {
    id: 3,
    text: 'Salary',
    amount: 200
  },
]);

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => acc + transaction.amount, 0);
});

const income = computed(() => {
  return transactions.value
  .filter(transaction => transaction.amount > 0)
  .reduce((acc, transaction) => acc + transaction.amount, 0)
  .toFixed(2);
});

console.info(income.value)

const expenses = computed(() => {
  return transactions.value
  .filter(transaction => transaction.amount < 0)
  .reduce((acc, transaction) => acc + transaction.amount, 0)
  .toFixed(2);
});
</script>

<template>
  <main-header></main-header>
  <main>
    <main-balance :total="total"></main-balance>
    <income-expense :income="+income" :expenses="+expenses"></income-expense>
    <transaction-list :transactions="transactions"></transaction-list>
    <transaction-add></transaction-add>
  </main>
</template>
