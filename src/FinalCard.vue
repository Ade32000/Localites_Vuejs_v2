<template>
    <div id="final" class="container">
        <div class="container">
            <div  class="card" style="width: 18rem;"
                    v-for="info in commune"
                    v-bind:key="info.code"
                    v-bind:value="info.code">

                <div v-if="nom === info.nom" class="card-body">
                    <h5 class="card-title">{{info.nom}}</h5>
                    <!-- <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6> -->
                    <p class="card-text">Population : {{info.population}}<br/>Surface : {{info.surface}}<br/>Département : {{info.departement.nom}}<br/>Région : {{info.region.nom}}</p>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import $ from 'jquery';

export default {

    name: 'final-card',
    data(){
        return{
            commune: [],
            nom: ""
        }
    },
    mounted: function(){
            this.$root.$on('updateCommune', data => 
            {
                console.log(data)
                $.ajax('https://geo.api.gouv.fr/communes?nom='+data+'&fields=nom,code,codesPostaux,surface,codeDepartement,departement,codeRegion,region,population&boost=population').done(function(d){
                    this.nom = data;
                    this.commune = d;
                    console.log(this.commune)
                }.bind(this))
            });        
    }
}
</script>

<style>
    @import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
    .card{
        margin: 0;
    }
    .container{
        /* margin-top: 1%; */
    }
</style>
