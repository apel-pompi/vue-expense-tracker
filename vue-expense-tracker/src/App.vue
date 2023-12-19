<template>
  <Header/>
  <div class="container">
    <Balance/>
    <IncomeExpense/>
    <TansactionList/>
    <AddTransaction/>
  </div>
</template>


<script>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TansactionList from "./components/TansactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
export default{
    components:{
        Header,
        Balance,
        IncomeExpense,
        TansactionList,
        AddTransaction,
    },
};
</script>


<style scoped>

</style>
