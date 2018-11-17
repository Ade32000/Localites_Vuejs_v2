<template>
    <div id="departements">
        <h2>Les départements</h2>
        <select v-model="selected"
                v-on:change="displayDepartements">
            <option disabled value="">Sélectionner un département</option>
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
                this.$root.$emit('updateDepartement', e.target.value)
                console.log('Département a envoyé le code :'+ e.target.value+' c\'est fun !')
            }
        },
        mounted: function(){
            this.$root.$on('updateRegion', data => 
            {
                console.log(data)
                $.ajax('https://geo.api.gouv.fr/regions/'+data+'/departements').done(function(d){
                console.log('ca marche')                   
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

</style>