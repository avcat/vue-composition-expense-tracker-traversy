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
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction;
  }, 0);
});
</script>

<template>
  <main-header></main-header>
  <main>
    <main-balance :total="total"></main-balance>
    <income-expense></income-expense>
    <transaction-list :transactions="transactions"></transaction-list>
    <transaction-add></transaction-add>
  </main>
</template>
