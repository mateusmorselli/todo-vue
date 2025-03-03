<script setup>
    const props = defineProps(['tarefas', 'filtro', 'tarefasFiltradas', 'tarefasFinalizadas']);
</script>

<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in tarefas">
          <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
          <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
            {{ tarefa.titulo }}
          </label>
        </li>
        <li class="list-group-item">
            <p v-if="filtro === 'pendentes' && tarefasFiltradas === 0">
                Nenhuma tarefa pendente
            </p>
            <p v-if="filtro === 'finalizadas' && tarefasFinalizadas === 0">
                Nenhuma tarefa finalizada
            </p>
        </li>     
    </ul>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
    color: red;
  }

  p {
    color: red;
    font-weight: bold;
  }
</style>
