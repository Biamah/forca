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
        :action="setDica"
      />

    </section>

    <section v-if="tela === 'jogo'" id="jogo">
      <Jogo
        :erros="erros"
        :palavra="palavra"
        :dica="dica"
        :verificaLetra="verificaLetra"
        :etapa="etapa"
        :letras="letras"
        :jogar="jogar"
        :jogarNovamente="jogarNovamente"
      />

      <Palavra />
    </section>
  </div>
</template>

<script>
import './css/global.css';
import Formulario from './components/Formulario.vue';
import Jogo from './components/Jogo.vue';
import Palavra from './components/Palavra.vue';

export default {
  name: 'App',
  data(){
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      erros: 0,
      letras: [],
    }
  },
  components: {
    Formulario,
    Jogo,
    Palavra,
  },
  methods: {
    setPalavra: function(palavra){
      this.palavra = palavra;
      this.etapa = 'dica';
    },
    setDica: function(dica){
      this.dica = dica;
      this.tela = 'jogo'
      this.etapa = 'jogo';
    },
    verificaLetra(letra){
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
    },
    jogar(letra){
      //adiciona letra jogada
      this.letras.push(letra);

      //validar erro
      this.verificaErro(letra);
    },
    verificaErro(letra){
      //acerto
      if(this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0){
        return this.verificaAcerto();
      }

      //erros
      this.erros++;

      //enforcado
      if(this.erros === 6){
        this.etapa = 'enforcado';
      }
    },
    verificaAcerto(){
      let letrasUnicas = [...new Set(this.palavra.split(''))];

      if(letrasUnicas.length === (this.letras.length - this.erros)){
        this.etapa = 'ganhador';
      }
    },
    jogarNovamente(){
      this.palavra = '';
      this.dica = '';
      this.erros = 0;
      this.letras = [];
      this.tela = 'inicio';
      this.etapa = 'palavra';
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
