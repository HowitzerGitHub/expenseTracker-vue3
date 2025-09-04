<template>
  <Header></Header>
  <div class="container">
    <Balance></Balance>
    <IncomeExpenses></IncomeExpenses>
    <TransactionList></TransactionList>
    <AddTransaction></AddTransaction>
  </div>
</template>
<script>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import addTransaction from "./components/addTransaction.vue";
import AddTransaction from "./components/addTransaction.vue";

export default {
  components: {
    Header,
    Balance,
    IncomeExpenses,
    TransactionList,
    AddTransaction,
  },
};
</script>

<style scoped></style>
