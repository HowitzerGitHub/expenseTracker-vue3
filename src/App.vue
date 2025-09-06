<template>
  <Header></Header>
  <div class="container">
    <Balance :total="total"></Balance>
    <IncomeExpenses :income="income" :expense="expense"></IncomeExpenses>
    <TransactionList
      :transactions="transactions"
      @transactionDeleted="onDeleteTransaction"
    ></TransactionList>
    <AddTransaction
      @transactionSubmitted="onTransactionSubmitted"
    ></AddTransaction>
  </div>
</template>
<script setup>
import { ref, computed } from "vue";
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/addTransaction.vue";
import { useToast } from "vue-toastification";

const toast = useToast();

const transactions = ref([
  { id: 1, text: "dog food", amount: -39.99 },
  { id: 2, text: "camera", amount: -150.99 },
  { id: 3, text: "laptop", amount: -199.99 },
  { id: 4, text: "salary", amount: 499.99 },
  { id: 5, text: "Book", amount: -19.99 },
]);
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
const income = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    if (transaction.amount > 0) return acc + transaction.amount;
    return acc;
  }, 0);
});
const expense = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    if (transaction.amount < 0) return acc + transaction.amount;
    return acc;
  }, 0);
});
const onTransactionSubmitted = (data) => {
  transactions.value.push({
    text: data.text,
    amount: data.amount,
    id: generateUniqueId(),
  });
  toast.success("Trasanction Added");
};
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};
const onDeleteTransaction = (id) => {
  const transactionIndex = transactions.value.findIndex((transaction) => {
    return transaction.id === id;
  });
  transactions.value.splice(transactionIndex, 1);
};
</script>

<style scoped></style>
