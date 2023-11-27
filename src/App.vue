<script>
  import MainHeader from './components/MainHeader.vue';
  import MainBalance from './components/MainBalance.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransactionList from './components/TransactionList.vue';
  import TransactionAdd from './components/TransactionAdd.vue';

  export default {
    components: {
      MainHeader,
      MainBalance,
      IncomeExpense,
      TransactionList,
      TransactionAdd
    }
  }
</script>

<template>
  <main-header></main-header>
  <main>
    <main-balance></main-balance>
    <income-expense></income-expense>
    <transaction-list></transaction-list>
    <transaction-add></transaction-add>
  </main>
</template>
