
<template>
    <input class ="input" v-model="result" />
    <p>{{ result }}</p>

</template>

<script setup> 

    import {ref} from 'vue';
    const result = ref("truc") 

</script>