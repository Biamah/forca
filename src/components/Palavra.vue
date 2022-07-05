<template>
  <div class="palavra">
    
    <div class="palavra__letras">
        <div class="palavra__letra" v-for="(letra, key) in palavra" :key="key">
            {{ (verificaLetra(letra) || etapa === 'enforcado') ? letra : '' }}
        </div>
    </div>

    <div class="palavra__dica">{{dica}}</div>

  </div>
</template>

<script>
export default {
    name: 'Palavra',
    props: {
        palavra: String,
        dica: String,
        verificaLetra: Function,
        etapa: String,
    },
    data(){

    },
    methods: {

    },
    components: {

    }
}
</script>

<style>
.palavra {
    text-transform: uppercase;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
}

.palavra__letras {
    display: flex;
    margin-bottom: 20px;
}

.palavra__letra {
    height: 25px;
    width: 30px;
    margin: 0 5px;
    border-bottom: 1px solid var(--color-text-light);
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>