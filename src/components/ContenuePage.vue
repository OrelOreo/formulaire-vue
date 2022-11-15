<template>

    <div class="container">

        <h1>Notre premier Formulaire</h1>
        <form>

            <div class="form-group">
                <label for="prenom">Ton prénom</label>
                <input v-on:input="toggleResult" v-model.lazy="formData.prenom" type="text" id="prenom" class="form-control">
            </div>

            <div class="form-group">
                <label for="txt">Ton texte</label>
                <textarea v-on:input="toggleResult" v-model.lazy="formData.txt" class="form-control" id="txt"></textarea>
            </div>

            <h3>Select Box</h3>

            <select v-model="formData.select">
                <option v-bind:key="index" v-for="(pays, index) in formData.listePays">{{ pays }}</option>
            </select>


            <h3 class="mt-3">CheckBoxs</h3>

            <div class="form-check">
                <input v-on:input="toggleResult" v-model="formData.checkFruits" value="pomme" id="pomme" type="checkbox" class="form-check-input">
                <label for="pomme">Pomme</label>
            </div>

            <div class="form-check">
                <input v-on:input="toggleResult" v-model="formData.checkFruits" value="citron" id="citron" type="checkbox" class="form-check-input">
                <label for="citron">Citron</label>
            </div>

            <div class="form-check">
                <input v-on:input="toggleResult" v-model="formData.checkFruits" value="fraise" id="fraise" type="checkbox" class="form-check-input">
                <label for="fraise">Fraise</label>
            </div>

           

            <button v-on:click.prevent="envoiForm" class="btn btn-primary mt-5">Envoyez les données</button>

            
        </form>
        <br>

        <div v-if="infoSubmit">

            <h2>Résultats</h2>
            
            <div class="card p-3">
                <p>Prénom : {{ formData.prenom }} </p>
                <p style="white-space: pre">Texte : {{ formData.txt }} </p>
                
                <p>Résultats checkboxs :</p>
                <ul>
                    <li v-bind:key="index" v-for="(fruit, index) in formData.checkFruits">{{ fruit }}</li>
                </ul>
                
                <p>Choix du select : {{ formData.select }}</p>
            </div>
            
        </div>
        
    </div>
</template>


<script>

export default {
    name: 'ContenuPage',
    data(){
        return {
            formData: {
                prenom: '',
                txt: '',
                checkFruits: [],
                select: '',
                listePays: ['Russie','Japon','Canada','Mexique']
            },
            infoSubmit: false
            
        }
    },
    methods: {
        envoiForm: function() {
            this.infoSubmit = true
        },
        toggleResult: function() {
            this.infoSubmit = false
        }
    }
}

</script>


<style>

li {
    width: 20%;
    margin: 0 auto;
}

</style>