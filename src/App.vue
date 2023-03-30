<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"></BarraLateral>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioCron @aoSalvarTarefa="salvarTarefa"></FormularioCron>
      <div class="lista">
        <TarefaTimer v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"></TarefaTimer>
      </div>
      <BoxTimer v-if="listaVazia">
        Sem tarefas
      </BoxTimer>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioCron from './components/FormularioCron.vue';
import TarefaTimer from './components/TarefaTimer.vue';
import ITarefa from './interfaces/ITarefa'
import BoxTimer from './components/BoxTimer.vue';

export default defineComponent({
  name: "App",
  components: { BarraLateral, FormularioCron, TarefaTimer, BoxTimer },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  },
  computed: {
    listaVazia(): boolean {
      return this.tarefas.length === 0
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background: var(--bg-primario);
}
</style>
