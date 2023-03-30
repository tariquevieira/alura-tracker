<template>
  <header>
    <h1>
      <img src="../assets/aluratracker.png" alt=" logo alura tracker">
    </h1>
    <button class="button" @click="alterarTema">{{ textoBotao }}</button>
  </header>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BarraLateral',
  emits: ['aoTemaAlterado'],
  data() {
    return {
      modoEscuroAtivo: false
    }
  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo;
      this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
    }
  },
  computed: {
    textoBotao() {
      if (this.modoEscuroAtivo) {
        return 'Desativar modo escuro'
      }
      return 'Ativer modo escuro'
    }
  }
})
</script>
<style scoped>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
}
</style>