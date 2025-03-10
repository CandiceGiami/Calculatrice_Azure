<template>
    <button :disabled="result === 0" @click="decremente">-</button>
    <button :disabled="result === 10 " @click="incremente">+</button>
    {{ result }}
    <div v-for = "(element,index) in myList" :key="index">
        <div :class="element.valeur === 0 ? 'red' : 'green'">{{ element.label }}</div>
    </div>
</template>

<script setup>
    import { ref,computed } from 'vue';
    const result = ref(0);
    const myList = ref([]);
    const decremente = () => {
        result.value --
        myList.value.push({label:new Date().toLocaleTimeString() + 'Décremente (-)',valeur:0})
    }
    const incremente = () => {
        result.value ++
        myList.value.push({label:new Date().toLocaleTimeString() + 'Incrémente (+)',valeur : 1})
    }

    const myListTrier = computed(() => { return [...myList.value].reverse})
</script>

<style scoped>

.red {
    color: red;
}
.green {
    color: rgb(0, 255, 21);
}
</style>