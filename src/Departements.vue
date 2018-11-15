<template>
    <div>
        <h2>Liste des départements français :</h2>
        <li v-for=" d in departements " v-bind:key="d.id">{{ d.nom }}</li>

    </div>
</template>


<script>
    import $ from 'jquery';

    export default {
        name: 'departements',
        data() {
            return{
                departements: []
            }
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/departements').done(function(d){
                this.departements = d;
            }.bind(this));
        }
        
    }
</script>


<style>

</style>