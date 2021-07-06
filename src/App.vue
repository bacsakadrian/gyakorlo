<template>
<head>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
</head>
<body style="text-align : center">
<input v-model.number="szam" type="number">
  <button :disabled="isinvalid" v-on:click="add" type="button">Klikk!</button>
  <h1>Az érték: {{ szam > 0 ? szam : "default" }}</h1>
  <h2>Második érték:{{ertek}}</h2>
<table class="table table-striped table-dark">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">oldVal</th>
      <th scope="col">newVal</th>
      <th scope="col">diff</th>
      <th scope="col">id</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="data in datas" :key="data">
      <th scope="row">{{data.idx}}</th>
      <td>{{data.oldVal}}</td>
      <td>{{data.newVal}}</td>
      <td>{{data.newVal - data.oldVal}}</td>
      <td>{{data.id}}</td>
      <button @click="remove(data.idx)" style="background-color : red" type="button">Törlés</button>
    </tr>
  </tbody>
  <tfoot style="text-align: center"> 
    Elemek száma: {{datas.length}}
  </tfoot>
</table>
</body>
<Info @my-event="reset" :num="ertek"></Info>
</template>

<script>
import Info from './components/Info.vue'
export default {
  name: 'App',
  components: { Info, },
  data() { 
    return {
    szam: 0,
    ertek: 0,
      datas : [ 
       {idx : 1, oldVal : 3, newVal: 4, id : new Date(2000,1,1)},
       {idx : 2, oldVal : 5, newVal : 6, id: new Date(2021,7,5) },
       {idx : 3, oldVal : 6, newVal : 13, id : new  Date(2022,8,4) },
       {idx : 4, oldVal : 20, newVal : 30, id : new Date(2023,3,2) }
       ]
    }
  },
    methods: {
      add: function() {
        this.ertek = this.ertek + this.szam
        alert(this.ertek) 
      },
      remove(index) { 
        for (let i = 0; i < this.datas.length; i++) { 
          if(this.datas[i].idx == index) {
            this.datas.splice(i, 1)
          }
        }
      },
      reset() {
        this.ertek = 0
      }
    },
    computed: {
      isinvalid() {
        return this.szam.length == 0 || this.szam < 0
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
  .example[data-v-f3f3eg9] {
    color: red;
  }
}
</style>