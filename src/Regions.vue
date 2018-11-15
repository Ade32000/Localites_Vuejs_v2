<template>
    <div id="regions">
        <h2>Liste des régions françaises :</h2>
        <li v-for=" r in regions " v-bind:key="r.id">{{ r.nom }}</li>
    </div>
</template>


<script>
    import $ from 'jquery';


    export default {
        name: 'regions',
        data() {
            return{
                regions: []
            }
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/regions').done(function(d){
                this.regions = d;
            }.bind(this));
        }
        
    }
    </script>


<style>

</style>

