<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="item">Item</label>
      <input type="text" id="item" placeholder="Enter text..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="notes">Notes</label>
      <input type="text" id="notes" placeholder="Add a desciption (optional)" v-model="notes" />
    </div>
    <div class="form-control">
      <label for="amount">Amount <br />
        (negative - expense, positive - income)</label>
      <input type="text" id="amount" placeholder="Enter amount..." v-model="amount" />
    </div>
    <button class="btn">Add transaction</button>
  </form>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';

const text = ref('');
const amount = ref('');
const notes = ref('');

// Get toast interface
const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!item.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error('Item and amount must be added.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
    notes: notes.value
  };

  emit('transactionSubmitted', transactionData);

  // Clear form fields
  text.value = '';
  amount.value = '';
  notes.value = '';
};
</script>