<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
    numberA: 0,
    numberB: 0,
    operation: '',
})

const resultado = computed(()=> {
  switch(estado.operation) {
      case 'somar':
      return estado.numberA + estado.numberB;
      case 'subtrair':
      return estado.numberA - estado.numberB;
      case 'multiplicar':
      return estado.numberA * estado.numberB;
      case 'dividir':
      return estado.numberB !== 0 ? estado.numberA / estado.numberB : 'Não é possivel dividir um numero por 0'
      default :
      return 0;
  }
})


</script>

<template>
  <div class="container">
  <header>
    <h1>Calculadora</h1>
  </header>
  <section>
      <input type="number" v-model.number="estado.numberA">
      <select v-model="estado.operation">
        <option value="somar">+</option>
        <option value="subtrair">-</option>
        <option value="multiplicar">x</option>
        <option value="dividir">%</option>
      </select>
      <input type="number" v-model.number="estado.numberB ">
      <br>
        <h2>Resultado: {{ resultado }}</h2>
    </section>
  </div>
</template>

<style scoped>
  .container{
    max-width: 600px;
    margin: 0 auto;
    text-align: center;
    padding: 80px 0;
    margin-top: 200px;
    background-color: rgb(201, 147, 252);
    border-radius: 10%;
    border: 3px solid rgb(135, 18, 231);
    font-family: sans-serif;
  }

  input {
    padding: 8px;
    max-width: 50px;
    border-color: rgb(189, 114, 250); 
    text-align: center;
  }

  select {
    margin-left: 6px;
    margin-right: 6px;
    border-color: rgb(189, 114, 250);
  }

  h1, h2{
    text-transform: uppercase;
    color: #fff;
  }

  input[type=number]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

</style>
