<script setup>
const { filtro, tarefasTemp } = props;
const { cadastroTarefas, trocarFiltro, editaTarefasTemp } = props;
</script>

<template>
    <form @submit.prevent="cadastroTarefas">
        <div class="row align-items-center">
            <div class="col-md-auto col-12">
                <input v-model="tarefasTemp" required type="text" placeholder="Descrição" class="form-control">
            </div>
            <div class="col-md-auto col-12">
                <button type="submit" class="btn btn-secondary">Cadastrar</button>
            </div>
            <div class="col-md-auto col-12 mt-2 mt-md-0">
                <select v-model="filtro" class="form-control" @change="trocarFiltro">
                    <option value="todas">Todas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>

<style scoped></style>