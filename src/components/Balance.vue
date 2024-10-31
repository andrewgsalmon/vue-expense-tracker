<template>
  <h4>Your Balance</h4>
  <h1 id="balance" :class="total < 0 ? 'negative-balance' : ''">${{ commaTotal }}</h1>
</template>

<script setup>
import { defineProps, computed } from 'vue';

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});

const commaTotal = computed(() => new Intl.NumberFormat(undefined, {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  }).format(props.total));
</script>
