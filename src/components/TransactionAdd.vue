<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification'

const title = ref('');
const amount = ref('');
const toast = useToast()
const emit = defineEmits([
  'transactionSubmitted'
])

const submit = (e) => {
  if (!title.value || !amount.value) {
    toast.error('Both fields must be filled!')
    return
  }

  const transactionData = {
    title: title.value,
    amount: parseFloat(amount.value)
  }

  emit(
    'transactionSubmitted',
    transactionData
  )
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
  </form>
</template>