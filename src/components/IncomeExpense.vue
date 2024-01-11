<script setup>
const props = defineProps({
  income: {
    type: Array,
    required: true,
  },
  expenses: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <div>
    <h2>Income</h2>
    <p>${{ income }}</p>
  </div>
  <div>
    <h2>Expense</h2>
    <p>${{ expenses }}</p>
  </div>
</template>