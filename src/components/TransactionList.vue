<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li v-if="transactions.length > 0" v-for="transaction in transactions" :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'">
      <div>{{ transaction.text }} <span class="transaction-date">- {{ transaction.date }}</span></div><span>${{ formatNumber(transaction.amount) }}</span>
      <button class="delete-btn" @click="deleteTransaction(transaction.id)">
        x
      </button>
    </li>
    <li v-else :key="0" class="transaction__pending">
      Submit a transaction below...
    </li>
  </ul>
</template>
<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
};

const formatNumber = (number) => {
  return new Intl.NumberFormat(undefined, {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  }).format(number);
};
</script>