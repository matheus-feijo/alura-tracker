<template>
<div class="box">
    <div class="columns">
        <div class="column is-8" role="form" aria-label="Formulario para criar novas tarefas">
            <input type="text" class="input" placeholder="qual tarefa voce deseja comecar?" />
        </div>

        <div class="column">
            <div class="is-flex is-align-items-center is-justify-content-space-between">
                <section>
                    <strong>{{tempoDecorrido}}</strong>
                </section>

                <button class="button" @click="start">
                    <span class="icon">
                        <i class="fas fa-play"></i>
                    </span>
                    <span>play</span>
                </button>

                <button class="button" @click="finish">
                    <span class="icon">
                        <i class="fas fa-stop"></i>
                    </span>
                    <span>stop</span>
                </button>
            </div>
            
        </div>
    </div>

</div>
</template>

<script lang="ts">
import {
    defineComponent
} from "vue"
export default defineComponent({
    name: "FormularioTask",
    data(){
        return{
            tempoEmSegundos:0,
            cronometro:0
        }
    },
    computed:{
        tempoDecorrido():string{
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
        }
    },
    methods: {
        start(){
            this.cronometro = setInterval(()=>{
                this.tempoEmSegundos +=1;
            },1000);
            console.log("inicio");
        },

        finish(){
            clearInterval(this.cronometro);
            console.log("fim");
        }
    },

})
</script>

<style>

</style>
