<template>
  <Header/>
  <div class="container">
    <Balance :total="+total"/>
    <IncomeExpense :income="+income" :expense="+expense"/>
    <TansactionList :transactions="transactions" @transactionDeleted="handleTransactionDeleted"/>
    <AddTransaction @transactionSumitted="handleTransactionSubmitted"/>
  </div>
</template>


<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TansactionList from "./components/TansactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref,computed } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast();

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

//add transaction
const handleTransactionSubmitted = (transactionData) => {
  //console.log(transactionData)
  transactions.value.push({
    id:generateUniqueId(),
    text:transactionData.text,
    amount:transactionData.amount
  });
  toast.success('Transaction added');
};

//generate unique id
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
}

//Deleted Transaction
const handleTransactionDeleted = (id)=>{
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id);
  toast.error('Transaction Deleted');
}
</script>


<style scoped>

</style>
