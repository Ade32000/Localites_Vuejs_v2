<template>
    <div id="regions">
        <div class="input-group mb-3">
            <div class="input-group-prepend">
                <label class="input-group-text" for="inputGroupSelect01">Les régions</label>
            </div>
            <select v-model="selected" 
                    v-on:change="displayRegions" class="custom-select" id="inputGroupSelect01">
                <option disabled value="">Sélectionner une région...</option>
                <option v-for="option in regions" 
                        v-bind:key="option.code" 
                        v-bind:value="option.code">
                        
                        {{ option.nom }} ({{ option.code }})
                </option>
                <!-- <span class="badge">{{departements.length}}</span> -->
            </select>
        </div>
    </div>
</template>


<script>
    import bootstrap from 'bootstrap'
    import $ from 'jquery';
    //import Bus from './Bus.js'
    
    export default {
        name: 'regions',
        data() {
            return{
                regions: [],
                selected:""
            }
        },
        methods: {
            displayRegions: function(e) {
                console.log(e.target.value)
                this.$root.$emit('updateRegion',e.target.value)
                console.log('Région a envoyé le code :'+ e.target.value+' c\'est cool !')
            }
        },
        created: function(){
                $.ajax('https://geo.api.gouv.fr/regions').done(function(d){
                    console.log(d[1].codeRegion)
                    this.regions = d;
                }.bind(this))
        }, 
    }

    </script>


<style>
    @import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
</style>

