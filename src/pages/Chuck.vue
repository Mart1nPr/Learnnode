<script setup>
import { ref } from 'vue';

let joke = ref(" ");

function reqListener() {
    let data = JSON.parse(this.responseText)
    console.log(data.value);
    joke.value = data.value;
}

const req = new XMLHttpRequest();
req.addEventListener("load", reqListener);
req.open("GET", "http://api.chucknorries.io/jokes/random");
req.send();


</script>

<template>
    {{ joke }}
</template>