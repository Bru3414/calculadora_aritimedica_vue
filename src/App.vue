<script setup>
import { reactive } from 'vue';

const estado = reactive({
  n1: 0,
  n2: 0,
  operador: '+',
})

const resolucao = () => {
  const { n1, n2, operador } = estado;

  switch (operador) {
    case '+':
      if (n1 === '' ||  n2 === '') {
        return 0
      } else {
        return parseInt(n1) + parseInt(n2);
      }

    case '-':
      if (n1 === '' ||  n2 === '') {
        return 0
      } else {
        return parseInt(n1) - parseInt(n2);
      }

    case '*':
      if (n1 === '' || n2 === '') {
        return 0
      } else {
        return parseInt(n1) * parseInt(n2);
      }

    case '/':
      if ((n1 === '' ||  n2 === '') || (n1 === 0 ||  n2 === 0)) {
        return 0
      } else {
        return parseInt(n1) / parseInt(n2);
      }

    default:
      return 0;
  }
}

</script>

<template>
  <div class="container">
    <div class="display">
      <div class="fundo">
        <h1>Calculadora aritimédica</h1>
        <div class="campos">
          <input value="0" @keyup="evento => estado.n1 = evento.target.value" type="number">
          <select @change="evento => estado.operador = evento.target.value" class="campos__operador">
            <option selected value="+">+</option>
            <option value="-">-</option>
            <option value="*">x</option>
            <option value="/">%</option>
          </select>
          <input value="0" @keyup="evento => estado.n2 = evento.target.value" type="number">
        </div>
        <span class="display__resultado">{{ resolucao() }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
