<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>

    <div class="column is-three-quarter conteudo">
      <Notificacoes />
      <router-view></router-view>
    </div>
  </main>
</template>

<script lang="ts">

import {defineComponent} from 'vue';
import BarraLateral from "@/components/BarraLateral.vue";
import Notificacoes from "@/components/Notificacoes.vue";

export default defineComponent({
  name: 'App',
  components: {Notificacoes, BarraLateral},

  data: () => ({
    modoEscuroAtivo: false,
  }),

  methods: {
    trocarTema(temaEscuroAtivo: boolean) {
      this.modoEscuroAtivo = temaEscuroAtivo;
    }
  }
});
</script>

<style>
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
