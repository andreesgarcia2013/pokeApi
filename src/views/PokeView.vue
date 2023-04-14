
<script setup>

import { useRoute, useRouter } from "vue-router";
import { useGetData } from '@/composables/getData'
import { useFavoritosStore } from '@/store/favoritos'
import { ref } from 'vue';
const route = useRoute()
const router = useRouter()
const useFavoritos = useFavoritosStore()

const {add, findPoke}=useFavoritos
const { data, getData, loading, errorData } = useGetData()


const back = () => {
    router.push('/pokemons')
}

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>
<template>
    <div v-if="loading">Cargando...</div>
    <div v-if="errorData" class="alert alert-danger">No existe el pokemon</div>
    <div v-if="data">
        <img :src="data.sprites?.front_default" alt="">
        <h1>pokemon name: {{ $route.params.name }}</h1>
        
        <button :disabled="findPoke(data.name)" class="btn btn-warning mb-2" @click="add(data)">Favorito</button>
    </div>
    <button class="btn btn-secondary" @click="back">back</button>
</template>