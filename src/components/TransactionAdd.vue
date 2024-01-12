<script setup>
import { ref } from 'vue';

const title = ref('');
const amount = ref('');

const submit = (e) => {
  console.info(title.value, amount.value)
}
</script>

<template>
  <form @submit.prevent="submit">
    <h2>Add new transaction</h2>
    <label>
      <h3>Title</h3>
      <input
        type="text"
        v-model="title"
      >
    </label>
    <label>
      <h3>Amount</h3>
      <input
        type="number"
        v-model="amount"
      >
      <small>Negative - expense, positive - income.</small>
    </label>
    <button type="submit">Submit</button>
</form></template>