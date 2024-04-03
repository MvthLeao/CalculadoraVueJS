<script setup>
import { reactive } from 'vue'; 

const estado = reactive({
  numero1: '',
  numero2: '',
  operador: 'adição',
  operacoes: {
    adicao: (numero1, numero2) => numero1 + numero2,
    subtracao: (numero1, numero2) => numero1 - numero2,
    divisao: (numero1, numero2) => numero1 / numero2,
    multiplicacao: (numero1, numero2) => numero1 * numero2,
  },
  resultado: 0,
});

const calcule = () => {
  const {numero1, numero2, operador} = estado;
  estado.resultado = estado.operacoes[operador](parseFloat(numero1), parseFloat(numero2));
};
</script>

<template>
  <div class="container">
    <h1>Calcule com VueJS</h1>
    <div class="calculadora">

      <input type="number" v-model="estado.numero1" @input="calcule">
      
      <select v-model="estado.operador" @change="calcule">
        <option value="adição">+</option>
        <option value="subtração">-</option>
        <option value="multiplicação">*</option>
        <option value="divisão">/</option>
      </select>
      
      <input type="number" v-model="estado.numero2" @input="calcule">

      <p>Resultado: {{ estado.resultado }}</p>
    </div>  
  </div>
</template>

<style scoped>
  body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
  }

  #app {
    text-align: center;
  }

  .calculator {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  input[type="number"], select, button {
    margin: 5px;
    padding: 5px;
  }

  input[type="text"] {
    margin: 10px;
    padding: 5px;
    width: 100px;
  }
</style>
