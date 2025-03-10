<template>
    <h1>Compteur Interactif</h1>

    <div v-if="compteur < 10">
        <button @click = "incrementer">+</button>
    </div>
    <div v-else>
        <button style="background-color: grey;">+</button>
    </div>

    <div v-if="compteur > 0">
        <button @click = "decrementer">-</button>
    </div>
    <div v-else>
        <button style="background-color: grey;">-</button>
    </div>

    <p>Compteur : {{ compteur }}</p>

    <h3>Historique des actions :</h3>
    <ul>
        <li v-for="(element,index) in historique" :key="index">{{ element }}</li>
    </ul>   

</template>

<script setup> 

    import {computed, ref} from 'vue';
    const compteur = ref(0);
    const actions = ref([]);
    const historique = computed(() => actions.value.reverse());
    function incrementer() {
        compteur.value ++;
        actions.value.push(new Date().toLocaleString() + " Incrémentation du compteur (+)")
    }
    function decrementer() {
        compteur.value --
        actions.value.push(new Date().toLocaleString() + " Décrémentation du compteur (-)")
    }

</script>
