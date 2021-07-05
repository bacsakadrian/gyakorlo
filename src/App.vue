<template>
  <input v-model.number="szam" type="number">
  <button v-on:click="add" type="button">Klikk!</button>
  <h1>Az érték: {{ szam > 0 ? szam : "default" }}</h1>
  <h2>Második érték:{{ertek}}</h2>
</template>

<script>

export default {
  name: 'App',
  data() {
      return {
        szam: 0,
        ertek: 0
      }
    },

    methods: {
      add: function() {
        this.ertek = this.ertek + this.szam
        alert(this.ertek) 
      }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
