<template>
  <h3>Add New Transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input type="text" id="text" placeholder="Enter Text..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="amount"
        >Amount <br />(negative - expense, positive - income)</label
      >
      <input
        type="number"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div>
    <button class="btn">Add Transaction</button>
  </form>
</template>

<script setup>
import { ref, defineModel } from "vue";
const amount = defineModel();
const text = defineModel();
const onSubmit = () => {};
</script>
