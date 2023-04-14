<script setup>
import { useFavoritosStore } from '@/store/favoritos'
import { storeToRefs } from 'pinia';
const useFavoritos = useFavoritosStore()
const { favoritos } = storeToRefs(useFavoritos)
const {remove}=useFavoritos
</script>

<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos==0" >Sin favoritos</p>
    <ul v-else class="list-group">
        <li v-for="poke in favoritos" :key="poke.id" class="list-group-item">
            {{ poke.name }}
            <div>
                <router-link :to="`/pokemons/${poke.name}`">
                    <button class="btn btn-success">Ver</button>
                </router-link>
                <button class="btn btn-danger" @click="remove(poke.id)">Eliminar</button>
            </div>
        </li>
    </ul>
</template>