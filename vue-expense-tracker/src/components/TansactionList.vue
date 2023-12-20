<template>
    <div class="transaction">
        <h3>History</h3>
        <ul id="list" class="list">
            <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount < 0 ? 'minus': 'plus'">
                {{transaction.text}} <span>-${{transaction.amount}}</span>
                <button class="delete-btn">x</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default{
    data() {
        return {
            transactions: [
                {id:1,text:'Flower',amount:-19.99},
                {id:2,text:'Salary',amount:119.00},
                {id:3,text:'Book',amount:-10.20},
                {id:4,text:'Camera',amount:200.00},
            ],
        };
    },
}
</script>


<style scoped>

</style>
