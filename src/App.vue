<script setup>
import { reactive } from 'vue';

const estado = reactive({
  primeiroNumero: 0,
  segundoNumero: 0,
  calcular: 'somar',
});

const {primeiroNumero, segundoNumero} = parseInt

const resultado = () =>{
const {calcular, primeiroNumero, segundoNumero} = estado;

    
  switch (calcular) {
    case 'somar':
      return (primeiroNumero + segundoNumero)
    case 'subtrair':
      return primeiroNumero - segundoNumero;
    case 'multiplicar':
      return primeiroNumero * segundoNumero;
    case 'dividir':
      return primeiroNumero !== 0 ? primeiroNumero / segundoNumero : 'Erro: Divisão por zero';
    default:
      return 0;
  }
}
</script>

<template>
  
<div class="container">
  <h1>Calculadora</h1>
    
    <label for="num1">Número 1: </label>
    <input type="number" @keyup="evento => estado.primeiroNumero = evento.target.value" placeholder="Digite o primeiro número" id="num1"> <br>
    
    <label for="num2">Número 2: </label>
    <input type="number" @keyup="evento => estado.segundoNumero = evento.target.value" placeholder="Digite o segundo número" id="num2"><br>
    
    <label for="operacao">Operação: </label>
    <select @change="evento => estado.calcular = evento.target.value" id="operacao">
      <option value="somar">Soma</option>
      <option value="subtrair">Subtração</option>
      <option value="multiplicar">Multiplicação</option>
      <option value="dividir">Divisão</option>
    </select>
    
    <p>Resultado: {{ resultado() }}</p>
  </div>

</template>


