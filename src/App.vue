<template>
  <div id="app">
    <MainSection @add='addExpenses($event)'/>
      <div class='row'>
      <p class='tableData'>Type</p>
      <p class='tableData'>Date</p>
      <p class='tableData'>Amount</p>
      <p class='tableData'>Button</p>
    </div>
     <transition-group name='slide'>
      <ExpenseTable
      v-for='item in expenses'
      :key='item.name'
      :name='item.name'
      :amount='item.amount'
      :day='item.day'
      :month='item.month'
      :date='item.date'
      @remove='removeExpense'
      />
    </transition-group>
 
      
     <h1>Summary:{{summary}} PLN</h1>
    
  </div>
  
</template>

<script>

import MainSection from './components/MainSection.vue';
import ExpenseTable from './components/ExpenseTable.vue'
export default {
  data: ()=>({
    expenses:[
      
    ],
  }),
  name: 'App',
  components: {
    MainSection,
    ExpenseTable,
  },
  methods:{
    removeExpense(){
     let nameIndex =  this.expenses.findIndex(expense => expense.name == name)
     this.expenses.splice(nameIndex, 1)
    },
    addExpenses(event){
      this.expenses.push(event)
    }
  },
  computed:{
    summary(){
        let total = 0
        this.expenses.forEach(expense  => total += parseInt(expense.amount))
        return total
    }
    
  }
}

</script>

<style>
*{
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.slide-enter-active, .slide-leave-active {
  transition: 0.87s
} 
.slide-enter, .slide-leave-to{
  opacity: 0;
  transform: translateX(30px)
}
</style>
