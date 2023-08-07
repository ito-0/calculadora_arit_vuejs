
<script setup>
import { ref, watch } from 'vue';
import CampoNumerico from './CampoNumerico.vue';
import CampoOperacao from './CampoOperacao.vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('soma');
const resultado = ref(0);

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
            resultado.value = numero1.value / numero2.value;
            break;
        default:
            resultado.value = 0;
    }
}

watch([numero1, numero2, operacao], calcular, { immediate: true });
</script>

<template>
    <div>
        <div class="row mb-3">
            <div class="col-md-4">
                <CampoNumerico v-model="numero1" />
            </div>
            <div class="col-md-4">
                <CampoOperacao v-model="operacao" />
            </div>
            <div class="col-md-4">
                <CampoNumerico v-model="numero2" />
            </div>
        </div>

        <p class="h3">Resultado: {{ resultado }}</p>
    </div>
</template>

<style scoped></style>