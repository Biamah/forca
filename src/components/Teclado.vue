<template>
  <div class="teclado">
    <button 
        class="teclado__botao" 
        v-for="(letra, key) in 'abcdefghijklmnopqrstuvwxyz'"
        :key="key"
        :disabled="verificaLetra(letra)"
        v-on:click="jogar(letra)"
    >{{letra}}</button>
  </div>
</template>

<script>
export default {
    name: 'Teclado',
    props: {
        letras: Array,
        verificaLetra: Function,
        jogar: Function,
    },
    data(){
        return
    },
    methods: {

    },
    components: {

    }

}
</script>

<style>
.teclado {
    padding-top: 30px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 80%;
}

.teclado__botao {
    margin: 4px;
    text-transform: uppercase;
}
</style>