<template>
  <div class="final">
    <div :class="`final__texto ${etapa}`">{{texto}}</div>

    <button class="final__botão" v-on:click="jogarNovamente">Jogar novamente</button>
  </div>
</template>

<script>
export default {
    name: 'Final',
    props: {
        etapa: String,
        texto: String,
        jogarNovamente: Function,
    }
}
</script>

<style>
.final__texto{
    margin: 20px 0;
    font-size: 24px;
    font-weight: 600;
}

.final__texto.enforcado {
    color: var(--color-text-error);
}

.final__texto.ganhador{
    color: var(--color-text-success);
}
</style>