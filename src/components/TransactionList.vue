<script setup>
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  }
})
</script>

<template>
  <div>
    <h2>Transactions</h2>
    <ul>
      <li
        v-for="t in transactions"
        :key="t.id"
        :class="{
          income: t.amount > 0,
          expense: t.amount < 0
        }"
      >
        <span>{{ t.text }}</span>
        <span>{{ t.amount }}</span>
        <button>Delete</button>
      </li>
    </ul>
  </div>
</template>