<template>
<div>
      <div class='row'>
      <p class='tableData'>{{name}}</p>
      <p class='tableData'>{{day}} {{month}} {{date.getFullYear()}}</p>
      <p class='tableData'>-{{amount}} PLN</p>
      <p class='tableData'><button class='removeButton' @click='remove'>Remove</button></p>
    </div>   
</div>
</template>

<script>

export default {
props:{
  name: String,
  amount: Number,
  day: String,
  month: String,
  date: Date,
},
methods:{
  remove(){
    this.$emit('remove', this.name)
  }
}
}

</script>

<style>
.row{
  margin: 0 auto;
  width: 60%;
  display: flex;
  justify-content: space-evenly;
  background-color: lightblue
}
.row:nth-of-type(odd){
  background-color: beige;
}
.tableData{
  width: 25%;
  padding-top: 20px;
  padding: 5px;
  box-sizing: content-box;
  font-weight: 700;
}
.removeButton{
  margin: 0;
  padding: 0;
}

</style>
