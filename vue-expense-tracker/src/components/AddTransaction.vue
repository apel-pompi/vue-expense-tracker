<template>
    <div class="addtransaction">
        <h3>Add new transaction</h3>
        <form id="form" @submit.prevent="onSubmit">
            <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter text..."/>
            </div>
            <div class="form-control">
            <label for="amount">Amount</label>
            <input
                type="text"
                id="amount"
                placeholder="Enter amount..."
               
            />
            </div>
            <button class="btn">Add transaction</button>
        </form>
    </div>
</template>

<script setup>

</script>


<style scoped>

</style>
