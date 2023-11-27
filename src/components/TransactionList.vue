<script>
export default {
  setup() {
    const transactions = [
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
    ];

    return {
      transactions,
    }
  }
}
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