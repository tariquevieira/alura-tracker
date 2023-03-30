<template>
  <BoxTimer>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa?.descricao || 'Sem descrição' }}
      </div>
      <div class="column">
        <CronometroTimer :tempoEmSegundos="tarefa?.duracaoEmSegundos" />
      </div>
    </div>
  </BoxTimer>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroTimer from './CronometroTimer.vue';
import ITarefa from '../interfaces/ITarefa';
import BoxTimer from './BoxTimer.vue';

export default defineComponent({
  name: "TarefaTimer",
  components: { CronometroTimer, BoxTimer },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      requeried: true
    }
  }
})
</script>
