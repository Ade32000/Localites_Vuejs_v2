<template>
        <div class="input-group mb-3">
            <div class="input-group-prepend">
                <label class="input-group-text" for="inputGroupSelect03">Les communes</label>
            </div>
            <select v-model="selected"
                    v-on:change="displayCommunes" class="custom-select" id="inputGroupSelect03">
                <option disabled value="">Sélectionner une commune...</option>
                <option v-for="option in communes" 
                        v-bind:key="option.code" 
                        v-bind:value="option.nom">
                            {{ option.nom }} ({{ option.code }})
                </option>
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
        methods: {
            displayCommunes: function(e){
                this.$root.$emit('updateCommune', e.target.value)
                console.log('Commune a envoyé le code :'+ e.target.value+' c\'est formidable !')
            }
        },
        mounted: function(){
            this.$root.$on('updateDepartement', data => 
            {
                $.ajax('https://geo.api.gouv.fr/departements/'+data+'/communes').done(function(d){
                this.communes = d;
                console.log('reçu 5 sur 5')
                }.bind(this))
            });        
        },
        created: function(){
            $.ajax('https://geo.api.gouv.fr/departements/01/communes').done(function(d){
                this.communes = d;
            }.bind(this));
        }
    }
</script>


<style>
    @import '../node_modules/bootstrap/dist/css/bootstrap.min.css';


</style>