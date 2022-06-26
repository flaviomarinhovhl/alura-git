<template>
    <BoxCentral>
        <div class="columns">
            <div class="colum is-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronometroCentral :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxCentral>

</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import CronometroCentral from "./CronometroCentral.vue";
import ITarefa from "@/interfaces/ITarefa";
import BoxCentral from "./BoxCentral.vue";

export default defineComponent({
    name: 'TarefaLista',
    components: {
    CronometroCentral,
    BoxCentral
},
    props:{
        tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

