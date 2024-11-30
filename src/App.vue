<template>
  <div class="centro">
    <div class="caixa">
      <h1>Calculadora VueJS</h1>
      <input v-model.number="estado.num1" @keyup="calcular" placeholder="Número 1">
      <select v-model="estado.operação" @change="calcular">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">x</option>
        <option value="/">/</option>
      </select>
      <input v-model.number="estado.num2" @keyup="calcular" placeholder="Número 2">
      <div class="resultado" v-if="estado.result !== null">
        <span>Resultado: {{ estado.result }}</span>
      </div>
    </div>
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
  if (estado.operação === '/' && estado.num2 === 0) {
    estado.result = 'Erro! Divisão por zero';
    return;
  }
  
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
  background-color: rgba(144, 238, 144, 0.567);
}
.caixa {
  padding: 20px;
  background-color: rgba(255, 255, 255, 0); 
  border: 2px solid rgba(1, 34, 12, 0.3); 
  border-radius: 10px; 
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.8); 
}

input, select {
  padding: 10px;  
  width: 120px;
  margin: 10px;
  font-size: 16px;
  background-color: rgba(255, 255, 255, 0);
  border: 1px solid rgba(0, 0, 0, 0.3);
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(2, 37, 24, 0.7);

}

input:focus, select:focus {
  outline: none;
  box-shadow: 0 0 10px rgba(2, 37, 24, 0.7);
}

.resultado {
  margin-top: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  ;
}

span {
  font-weight: bold;
  margin: 12px;
  font-size: 18px;
  color: #000000;
}

h1 {
  margin-bottom: 20px;
}
</style>

