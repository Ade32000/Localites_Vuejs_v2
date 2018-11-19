<template>
        <div class="input-group mb-3">
            <div class="input-group-prepend">
                <label class="input-group-text" for="inputGroupSelect02">Les départements</label>
            </div>
            <select v-model="selected"
                    v-on:change="displayDepartements" class="custom-select" id="inputGroupSelect02">
                <option disabled value="">Sélectionner un département...</option>
                <option v-for="option in departements" 
                        v-bind:key="option.code" 
                        v-bind:value="option.code"> 

                            {{ option.nom }} ({{ option.code }})
                        
                </option>
            </select>
        </div>
</template>


<script>
    import $ from 'jquery';

    export default {
        name: 'departements',
        data() {
            return{
                departements: [],
                selected:""
            }
        },
        methods: {
            displayDepartements: function(e){
                console.log(e.target.length)
                this.$root.$emit('updateDepartement', e.target.value)
                console.log('Département a envoyé le code :'+ e.target.value+' c\'est fun !')
            }
        },
        mounted: function(){
            this.$root.$on('updateRegion', data => 
            {
                console.log(data)
                $.ajax('https://geo.api.gouv.fr/regions/'+data+'/departements').done(function(d){
                console.log('ça marche')                   
                this.departements = d;
                }.bind(this))
            });        
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/departements').done(function(d){
                this.departements = d;
            }.bind(this));
        }  
    }


</script>


<style>
    @import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
</style>