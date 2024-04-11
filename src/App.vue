<script setup>
import { reactive } from 'vue'; 

const estado = reactive({
  numero1: '',
  numero2: '',
  operador: 'adição',
  operacoes: {
    adição: (numero1, numero2) => numero1 + numero2,
    subtração: (numero1, numero2) => numero1 - numero2,
    divisão: (numero1, numero2) => numero1 / numero2,
    multiplicação: (numero1, numero2) => numero1 * numero2,
  },
  resultado: 0,
});

const calcule = () => {
  const { numero1, numero2, operador } = estado;
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
  h1 {
    margin: 30px;
    color: green;
  }

  .calculadora, h1 {
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
