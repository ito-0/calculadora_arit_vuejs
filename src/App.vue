<script setup>
import { ref, watch } from 'vue';

const numero1 = ref();
const numero2 = ref();
const operacao = ref('soma');
const resultado = ref();

function calcular() {
  switch (operacao.value) {
    case 'soma':
      resultado.value = numero1.value + numero2.value;
      break;
    case 'subtracao':
      resultado.value = numero1.value - numero2.value;
      break;
    case 'multiplicacao':
      resultado.value = numero1.value * numero2.value;
      break;
    case 'divisao':
      if (numero2.value === 0) {
        resultado.value = 'ERRO';
      } else {
        resultado.value = numero1.value / numero2.value;
      }
      break;
    default:
      resultado.value = 0;
  }
}

watch([numero1, numero2, operacao], calcular, { immediate: true });

</script>

<template>
    <div class="d-flex justify-content-center align-items-center">
      <div class="calculator text-center">
        <h1>Ito's Calculator</h1>
        <div class="row mt-3 justify-content-center">
          <div class="col-sm-4 mb-3">
            <input v-model="numero1" type="number" class="form-control form-control-lg input-large" @input="calcular" placeholder="1º nº">
          </div>
          <div class="col-sm-2 mb-3 d-flex align-items-center justify-content-center">
            <select v-model="operacao" class="form-select" @change="calcular">
              <option value="soma">+</option>
              <option value="subtracao">-</option>
              <option value="multiplicacao">*</option>
              <option value="divisao">/</option>
            </select>
          </div>
          <div class="col-sm-4">
            <input v-model="numero2" type="number" class="form-control form-control-lg input-large" @input="calcular" placeholder="2º nº">
          </div>
        </div>

        <p class="h3">
          <h2 class="mt-3 mb-3">Resultado:</h2>
          <span class="result" v-if="resultado !== 'ERRO'">{{ resultado }}</span>
          <span class="error" v-else>ERRO</span>
        </p>
      </div>
    </div>
</template>

<style scoped>

.calculator {
  font-family: 'Roboto', sans-serif;
  padding: 24px;
  border: 2px solid #555;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: #333; 
  color: #f9f9f9; 
  max-width: 100%;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.calculator .form-select {
  width: 90px;
  height: 100%;
  padding: 10px;
  font-size: 36px;
  background-color: #3a3a3a;
  color: #fff;
  border: 7px solid #555;
  border-radius: 25px;
}

.calculator .form-select option {
  background-color: #444;
  color: #fff;
  border: 2px solid #555;
  text-align: center;
}

.calculator .result {
  font-size: 24px;
  color: #1E88E5;
  background-color: #202020;
  border-radius: 25px;
  padding: 10px;
}

.calculator .error {
  font-size: 36px;
  color: #ff0000;
}

.input-large {
  font-size: 22px;
  text-align: center;
  background-color: #1E88E5;
  border-radius: 25px;
  border-style: none;
}
</style>