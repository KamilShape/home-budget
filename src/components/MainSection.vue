<template>
<div class='container'>
  <h1>Expense calculator</h1>
  <div class='inputs'>
  <label for="">
    <p>Type of Expense</p>
  <input v-model = name type="text">
  </label>
    <label for="">
    <p>Date</p>
    <div class=dateContainer>
 <select v-model = day class='dateInput dayInput'>
   <option v-for='day in days' :key='day'>{{day}}</option>
 </select>
  <select v-model = month class='dateInput monthInput'>
   <option v-for='month in months' :key='month'>{{month}}</option>
 </select>
  <p class='yearInput'>{{date.getFullYear()}}</p>
  </div>
  </label>
    <label for="">
   <p>Amount</p> 
  <input v-model = amount type="number">
  </label>
  <div class='buttons'>
      <button @click='addExpense'>Add</button>
      <button @click='resetAll'>Reset</button>
  </div>
  </div>
</div>
</template>

<script>
export default {
data: ()=>({
  date: new Date,
  name: '',
  day: '',
  month: '',
  amount: '',
  days:[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31],
  months: ['January','February','March','April','May','June','July', 'August','September','October','November','December'],
}),
methods:{
  addExpense(){
    if(this.name !== '' && this.date !== '' && this.amount !== '' ){
       this.$emit('add',{
        name: this.name,
        day: this.day,
        month: this.month,
        amount: this.amount,
        date: this.date,
      },)
      this.resetAll()
    }else{
      return
    }
  
  },
  resetAll() {
     this.name = '',
     this.amount = '',
     this.day = '',
     this.month = ''
  },
}
}

</script>

<style>
h1{
  margin-bottom: 10px;
}
.inputs{
  margin: 0 auto;
  width: 60%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
label{
  width: 50%;
  display: flex;
  flex-direction: column;
  margin: 3px auto;
  align-self: space-between;
}
button{
  margin: 10px auto;
  padding: 5px;
  width: 100px;
  border-radius: 0 5px 0 5px;
  outline: none;
  font-weight: 700;
  background-color: beige;
}
input, select{
  display: flex;
  margin: 5px auto;
  width: 50%;
  text-align: center;
  padding: 3px;
}
select{
  display: block;
  padding: 3px;
  margin: 5px auto;
}
.dateContainer{
  display: flex;
  margin: 0 auto;
  justify-content: space-between;
  width: 50%;
}
.dayInput{
  width: 15%;
}
.dayInput{
  width: 20%;
}
.yearInput{
   text-align: center;
     margin: 5px auto;
      padding: 3px;
 }

button:hover {
    cursor: pointer;
    border-radius: 5px 0 5px 0;
    color: white;
    background-color: indianred;
}
.buttons {
  margin: 0 auto;
  width: 30%;
  display: flex;
  justify-content: space-evenly;
}
</style>
