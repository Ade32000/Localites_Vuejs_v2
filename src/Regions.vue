<template>
    <div id="regions">
        <h2>Les régions</h2>
        <select v-model="selected">
            <option disabled value="">Sélectionner une région</option>
            <option v-for="option in regions" v-bind:key="option.code" v-bind:value="option.code">{{ option.nom }} ({{ option.code }})</option>
        </select>
    </div>
</template>


<script>
    import $ from 'jquery';
    import Bus from './Bus.js'


    export default {
        name: 'regions',
        data() {
            return{
                regions: [],
                selected:""
            }
        },
        created: function(){
                $.ajax('https://geo.api.gouv.fr/regions').done(function(d){
                    this.regions = d;
                }.bind(this))
        },
            // this.displayRegions()

            // Bus.$emit('some-event')
            
        
        methods: {
            displayRegions: function () {
            console.log('hello from mixin!')
    }
  }
        
    }
    </script>


<style>

</style>

