<template>
  <div id="app">
    <h1>Jogo da Forca</h1>

    <section v-if="tela === 'inicio'" id="inicio">
      
      <Formulario v-if="etapa === 'palavra'"
        title="Defina a Palavra" 
        button="Próximo"
        :action="setPalavra" 
      />

      <Formulario v-if="etapa === 'dica'"
        title="Defina a Dica" 
        button="Iniciar o jogo" 
      />

    </section>

    <section v-if="tela === 'jogo'" id="jogo">
      Jogo
    </section>
  </div>
</template>

<script>
import './css/global.css';
import Formulario from './components/Formulario.vue';

export default {
  name: 'App',
  data(){
    return {
      tela: 'inicio',
      etapa: 'palavra',
    }
  },
  components: {
    Formulario,
  },
  methods: {
    setPalavra: function(palavra){
      alert(palavra);
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
