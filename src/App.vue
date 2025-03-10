<template>
  <div id="app">
     <!--
      <correction />
      <TextInput />
      <CompteurInteractif />
    -->
    <Calculatrice />
  </div>
</template>

<script setup>
import Calculatrice from "./components/Calculatrice.vue";
import TextInput from './components/TextInput.vue'
import CompteurInteractif from './components/CompteurInteractif.vue'
import correction from './components/correction.vue'
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  background: linear-gradient(to bottom right, #ffe6f2, #e6ffe6);
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
