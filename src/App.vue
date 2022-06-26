<template>
<main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">
<div class="column is-one-quarter">
  <BarraLateral @ao-tema-alterado="trocarTema"/>
</div>
<div class="column is-tree-quarter conteudo">
<FormularioLateral @aoSalvarTarefa="salvarTarefa"/>
<div class="lista">
  <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
  <BoxCentral v-if="listaEstaVazia">
Você não está muito produtivo sempre :)
</BoxCentral>
</div>

</div>
</main>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioLateral   from './components/FormularioLateral.vue';
import TarefaLista from './components/TarefaLista.vue';
import ITarefa from './interfaces/ITarefa';
import BoxCentral from './components/BoxCentral.vue';

export default defineComponent({
    name: "App",
    components: { BarraLateral, FormularioLateral, TarefaLista, BoxCentral },
    data(){
      return{
        tarefas:[] as ITarefa[],
        modoEscuroAtivo: false
      }
    },
    computed: {
      listaEstaVazia(): boolean{
        return this.tarefas.length ===0
      }
    },


    methods:{
      salvarTarefa(tarefa: ITarefa){
        this.tarefas.push(tarefa)
      },
      trocarTema(modoEscuroAtivo:boolean){
          this.modoEscuroAtivo=modoEscuroAtivo
      }
    }



});
</script>

<style>
.lista{
    padding: 1.25rem ;
}

main{
  --bg-primario:#fff;
  --texto-primario:#000;
}

main.modo-escuro{
--bg-primario:#2b2d42;
--texto-primario:#ddd;

}

.conteudo{
  background-color: var(--bg-primario);
}



</style>
