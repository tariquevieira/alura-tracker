<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTimer :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="status">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!status">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTimer from './CronometroTimer.vue';

export default defineComponent({
  name: "TemporizadorTimer",
  emits: ['aoTemporizadorFinalizado'],
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      status: false
    };
  },
  methods: {
    iniciar() {
      this.status = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      this.status = false;
      console.log("Finalizando");
      clearInterval(this.cronometro);
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0;
    }
  },
  components: { CronometroTimer }
})
</script>
<style></style>