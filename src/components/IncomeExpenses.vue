<template>
  <div class="inc-exp-container">
    <div>
      <h4>Income</h4>
      <p id="money-plus" :class="props.income > 0 ? 'money plus' : 'money'">{{ props.income > 0 ? `+$${formatNumber(props.income)}` : '--' }}</p>
    </div>
    <div>
      <h4>Expenses</h4>
      <p id="money-minus" :class="props.expenses < 0 ? 'money minus' : 'money'">{{ props.expenses < 0 ? `$${formatNumber(props.expenses)}` : '--'}}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});

const formatNumber = (number) => {
  return new Intl.NumberFormat(undefined, {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  }).format(number);
};

</script>
