<script setup>
import { ref, computed } from 'vue';
import { useToast } from 'vue-toastification'

import MainHeader from './components/MainHeader.vue';
import MainBalance from './components/MainBalance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import TransactionAdd from './components/TransactionAdd.vue';

const toast = useToast()

const transactions = ref([
  { 
    id: 1,
    title: 'Flowers',
    amount: -20
  },
  {
    id: 2,
    title: 'Book',
    amount: -20
  },
  {
    id: 3,
    title: 'Salary',
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

const expenses = computed(() => {
  return transactions.value
  .filter(transaction => transaction.amount < 0)
  .reduce((acc, transaction) => acc + transaction.amount, 0)
  .toFixed(2);
});

const generateUniqueID = () => Math.floor(
  Math.random() * 10**6
)

const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: generateUniqueID(),
    title: transactionData.title,
    amount: transactionData.amount,
  })

  toast.success('Transaction added: ' + transactionData.title)
}
</script>

<template>
  <main-header></main-header>
  <main>
    <main-balance :total="+total"></main-balance>
    <income-expense :income="+income" :expenses="+expenses"></income-expense>
    <transaction-list :transactions="transactions"></transaction-list>
    <transaction-add @transaction-submitted="handleTransactionSubmitted"></transaction-add>
  </main>
</template>
