<script setup>

import {ref} from 'vue'

import axios from 'axios'

var pokeSearch = defineModel()

var pokeObject = ref()

async function getPokemon(){

var response = await axios.get('https://pokeapi.co/api/v2/pokemon' + pokeSearch.value)

pokeObject.value = response.data

// console.log(pokeObject.value)

}

</script>

<template>

<h1>Poke api</h1>

<!-- <p>{{ pokeSearch }}</p> -->

<input type="text" v-model="pokeSearch">

<button @click="getPokemon">Get Pokemon</button>

<div v-if="pokeObject">

<h2>{{ pokeObject.name }}</h2>

<img :src="pokeObject.sprites.front_default" alt="">

</div>

</template>
