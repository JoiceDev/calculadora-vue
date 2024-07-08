<template>
  <div class="centro">
    <h1>Calculadora VueJS</h1>
    <input v-model.number="estado.num1" @keyup="calcular">
    <select v-model="estado.operação" @change="calcular">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">x</option>
      <option value="/">/</option>
    </select>
    <input v-model.number="estado.num2" @keyup="calcular">
    <span>Resultado: {{ estado.result }}</span>
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operação: '+',
  result: null
});

const calcular = () => {
  switch (estado.operação) {
    case '+':
      estado.result = estado.num1 + estado.num2;
      break;
    case '-':
      estado.result = estado.num1 - estado.num2;
      break;
    case '*':
      estado.result = estado.num1 * estado.num2;
      break;
    case '/':
      estado.result = estado.num1 / estado.num2;
      break;
    default:
      estado.result = null;
      break;
  }
};
</script>

<style scoped>

.centro {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh; 
  text-align: center;
  background-color: rgba(144, 238, 144, 0.758);
}

input, select {
  padding: 4px;
  width: 50px;
  margin: 6px;
}

span {
  font-weight: bold;
  margin: 8px;
}
</style>
