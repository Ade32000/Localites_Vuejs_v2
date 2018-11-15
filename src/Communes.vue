<template>
    <div>
        <h2>Liste des communes françaises :</h2>
        <li v-for=" c in communes " v-bind:key="c.id">{{ c.nom }}</li>
    </div>
</template>


<script>
    import $ from 'jquery';

    export default {
        name: 'communes',
        data() {
            return{
                communes: []
            }
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/departements/01/communes').done(function(d){
                this.communes = d;
            }.bind(this));
        }
    }
</script>


<style>

</style>