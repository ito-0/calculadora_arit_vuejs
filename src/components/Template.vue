<script setup>
import { ref } from 'vue';

const valor = ref(0);

function atualizarValor(event) {
    valor.value = event.target.value;
}
</script>

<template>
    <input v-model="valor" type="number" class="form-control" @input="atualizarValor">
</template>

<style scoped>
</style>