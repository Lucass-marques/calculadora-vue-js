<script setup>
import { reactive, watch } from 'vue';

const state = reactive({
  data: {
    valor1: 0,
    valor2: 0,
    operacao: '',
    resultado: 0
  }
});

watch(() => [state.data.valor1, state.data.valor2, state.data.operacao], () => {
  switch (state.data.operacao) {
    case 'somar':
      state.data.resultado = parseFloat(state.data.valor1) + parseFloat(state.data.valor2);
      break;
    case 'subtrair':
      state.data.resultado = parseFloat(state.data.valor1) - parseFloat(state.data.valor2);
      break;
    case 'multiplicar':
      state.data.resultado = parseFloat(state.data.valor1) * parseFloat(state.data.valor2);
      break;
    case 'dividir':
      state.data.resultado = parseFloat(state.data.valor1) / parseFloat(state.data.valor2);
      break;
    default:
      state.data.resultado = 0;
  }
});
</script>

<template>
  <div class="container">
    <header class="mt-5 p-4 rounded-3 bg-light">
      <h1>Calculadora</h1>
      <p>
        Coloque dois valores, a operação e o app fará a operação para você!
      </p>
    </header>

    <form class="mt-4">
      <div class="row">
        <div class="col">
          <input type="number" placeholder="Digite o 1° número" class="form-action" min="0" v-model="state.data.valor1">
        </div>
      </div>
      <div class="row mt-3">
        <div class="col">
          <input type="number" placeholder="Digite o 2° número" class="form-action" min="0" v-model="state.data.valor2">
        </div>
        <div class="col-10">
          <select v-model="state.data.operacao" class="form-action p-1 mt-3">
            <option value="somar">+</option>
            <option value="subtrair">-</option>
            <option value="multiplicar">*</option>
            <option value="dividir">/</option>
          </select>
        </div>
      </div>
    </form>

    <div class="row mt-3">
      <div class="col">
        <h3>O valor é: {{ state.data.resultado }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
