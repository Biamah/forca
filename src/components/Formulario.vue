<template>
  <div class="formulario">
    <div class="formulario__title">{{ title }}</div>

    <input type="text" class="formulario__input" v-model="inputValue">

    <button 
        :disabled="inputValue.length === 0"
        v-on:click="onSubmit"
    >{{ button }}</button>
  </div>
</template>

<script>
export default {
    name: 'Formulario',
    props: {
        title: String,
        button: String,
        action: Function,
    },
    data() {
        return {
            inputValue: ''
        }
    },
    methods:{
        onSubmit: function(){
            this.action(this.inputValue);
            this.inputValue = '';
        }
    },
}
</script>

<style>
.formulario {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    margin-top: 20px;
}

.formulario__input {
    padding: 10px 5px;
    border: 0;
    border-radius: 5px;
    margin: 10px 0;
    text-align: center;
    color: var(--color-text-dark);
    font-size: 16px;
}
</style>