<template>
  <div>
    <div >
      <input readonly placeholder="number1" v-model="input.number1.value" />
      <input readonly placeholder="number2"  v-model="input.number2.value" />
      =
      <input readonly placeholder="result"  v-model="input.result.value" />
      
    </div>
    <div>Číslo 1: {{ input.number1.value }}</div>
    <div>Číslo 2: {{ input.number2.value }}</div>
    <div>Výsledok: {{ input.result.value }}</div>
    <div class="buttonHolder">
      <NumberButton @numberButtonWasClicked="changeNumber"  :number="number" v-for="number of allNumbers" :key="number.id"/>
    </div>
    <div class="buttonHolder">
      <div class="button" v-on:click="execute1()">+</div>
      <div class="button" v-on:click="execute2()">-</div>
      <div class="button" v-on:click="execute3()">*</div>
      <div class="button" v-on:click="execute4()">/</div>
      <div class="button" v-on:click="execute5()">=</div>
    </div>
  </div>
</template>

<script setup>


const input = {status: "number1",number1: ref(""),number2: ref(""),operatin: "+",result: ref(0)};

const allNumbers = [{name: 1, id:1}, {name: 2, id:2}, {name: 3, id:3}, {name: 4, id:4}, {name: 5, id:5}, {name: 6, id:6}, {name: 7,id:7},{name: 8,id:8}, {name: 9,id:9}, {name: 0,id:0}]

const execute1=()=>{
  input.status = "number2";
  input.operatin = "+"
  console.log(input.status);
}
const execute2=()=>{
  input.status = "number2";
  input.operatin = "-"
  console.log(input.status);
}
const execute3=()=>{
  input.status = "number2";
  input.operatin = "*"
  console.log(input.status);
}
const execute4=()=>{
  input.status = "number2";
  input.operatin = "/"
  console.log(input.status);
}
const execute5=()=>{
  let num1 = Number(input.number1.value);
  console.log(num1);
  let num2 = Number(input.number2.value);
  console.log(num2);
  if (input.operatin == "+") {
    input.result.value = num1 + num2;
  } else if (input.operatin == "-") {
    input.result.value = num1 - num2;
  }  else if (input.operatin == "*") {
    input.result.value = num1 - num2;
  }  else{
    input.result.value = num1 / num2;
  }
  input.number1.value = "";
  input.number2.value = "";
  input.status = "number1";
  console.log(input.status);
}

const changeNumber  = (buttonCard)=>{
  if(input.status == "number1"){
    input.number1.value = input.number1.value + buttonCard.name;
  }else{
    input.number2.value = input.number2.value + buttonCard.name;
  }
}
</script>
<style>
  .button{
    width: 2rem;
    height: 2rem;
    margin-left: 1rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
    background-color: gray;
    color: white;
    float:left;
    text-align: center;
  }
</style>