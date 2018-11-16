<template>
    <div id="communes">
        <h2>Les communes</h2>
        <select v-model="selected">
            <option disabled value="">Sélectionner une commune</option>
            <option v-for="option in communes" v-bind:key="option.code" v-bind:value="option.code">{{ option.nom }} ({{ option.code }})</option>
        </select>
    </div>
</template>


<script>
    import $ from 'jquery';

    export default {
        name: 'communes',
        data() {
            return{
                communes: [],
                selected:""
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