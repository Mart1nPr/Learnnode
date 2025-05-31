<script setup>
import { ref } from 'vue';
import LeafletMap from '../components/LeafletMap.vue';

let center = ref([59.437216, 24.745369]);
let zoom = ref(19);

</script>
<template>
    <button class="button is-primary" @click="center = [59.42686, 24.74353]">School</button>
    <button class="button is-primary" @click="center = [59.415851, 24.799275]">Home</button>
    <input type="range" min="1" max="19" v-model="zoom">
    <LeafletMap :center="center" :zoom="zoom"></LeafletMap>
</template>