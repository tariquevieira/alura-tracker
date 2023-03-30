<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column" role="form" aria-label="formulario para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
      </div>
      <div class="column">
        <TemporizadorTimer @aoTemporizadorFinalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTimer from './TemporizadorTimer.vue'

export default defineComponent({
  name: "FormularioCron",
  emits: ['aoSalvarTarefa'],
  components: { TemporizadorTimer },
  data() {
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number): void {
      console.log(tempoDecorrido);
      console.log(this.descricao);
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = '';
    }
  }
})
</script>
<style>
.formulario {
  background: var(--bg-primario);
  color: var(--texto-primario);
}
</style>