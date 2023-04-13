<script setup>
import { ref } from 'vue';
import { RouterLink } from 'vue-router'
import { useGetData } from '@/composables/getData'
// const pokemons=ref([])

const { data, getData, loading, errorData } = useGetData()
// const getData=async()=>{
//     try {
//         const {data}= await axios.get('https://pokeapi.co/api/v2/pokemon')
//         pokemons.value=data.results
//     } catch (error) {
//         console.log(error);
//     }
// }
getData("https://pokeapi.co/api/v2/pokemon");
</script>
<template>
    <h1>Pokemons</h1>
    <div v-if="loading">Cargando...</div>
    <div v-if="errorData" class="alert alert-danger">{{ errorData }}</div>
    <div v-if="data">
        <button :disabled="!data.previous" class="btn btn-outline-primary" @click="getData(data.previous)"> prev</button>
        <button :disabled="!data.next" class="btn btn-outline-primary me-3" @click="getData(data.next)"> next</button>
        <div v-for="pokemon in data.results">
            <h1>
                <router-link :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</router-link>
            </h1>
        </div>        
    </div>
</template>