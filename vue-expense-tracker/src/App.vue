<template>
  <Header/>
  <div class="container">
    <Balance :total="total"/>
    <IncomeExpense :income="income" :expense="expense"/>
    <TansactionList :transactions="transactions"/>
    <AddTransaction/>
  </div>
</template>


<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TansactionList from "./components/TansactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref,computed } from "vue";

const transactions = ref([
        {id:1,text:'Flower',amount:-19.99},
        {id:2,text:'Salary',amount:119.00},
        {id:3,text:'Book',amount:-10.20},
        {id:4,text:'Camera',amount:200.00},
    ]);
//get total
const total = computed(()=>{
  return transactions.value.reduce((acc,transaction)=>{
    return acc + transaction.amount;
  }, 0)
});

//get income
const income = computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.amount >0)
  .reduce((acc,transaction)=>{
    return acc + transaction.amount;
  }, 0).toFixed(2);
});
//get expense
const expense = computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.amount < 0)
  .reduce((acc,transaction)=>{
    return acc + transaction.amount;
  }, 0).toFixed(2);
});
</script>


<style scoped>

</style>
