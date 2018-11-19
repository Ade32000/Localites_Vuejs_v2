<template>
  <div id="app" class="container">
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
import Chargement from './Chargement'

// const AsyncComponent = () => ({
//   // Le composant à charger (doit être une `Promise`)
//   component: import('./Regions')
//   // Un composant à utiliser pendant que le composant asynchrone se charge
//   loading: Chargement,
//   // Un composant d'erreur à utiliser au cas où le chargement échoue
//   error: ErrorComponent,
//   // Le délai à patienter avant d'afficher le composant de chargement. Par défaut : 200ms.
//   delay: 200,
//   // Le composant d'erreur sera affiché si un délai de timeout est fourni et dépassé.
//   // Par défaut: délai infini.
//   timeout: 3000
// })

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
    FinalCard,
    Chargement
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
  margin-bottom: 20%;
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
.container{
  margin-top: 30% !important;
}
</style>
