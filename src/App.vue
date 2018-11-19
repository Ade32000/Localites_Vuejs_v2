<template>
  <div id="app">
    <h1>HA.PP.Y :-) Open Data</h1>
    <regions></regions>
    <departements></departements>
    <communes></communes>
    <final-card></final-card>
  </div>
</template>

<script>
import bootstrap from 'bootstrap'
import Regions from './Regions'
import Departements from './Departements'
import Communes from './Communes'
import FinalCard from './FinalCard'


export default {
  name: 'app',
  data () {
    return {
      msg: 'hello world'
    }
  },
  components: {
    Regions,
    Departements,
    Communes,
    FinalCard
  }
}
</script>

<style>
@import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
