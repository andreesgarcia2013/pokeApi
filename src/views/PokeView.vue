import axios from 'axios';
<script setup>
    // import axios from 'axios';
    import { useRoute, useRouter } from "vue-router";
    import {useGetData} from '@/composables/getData'
import { ref } from 'vue';
    const route= useRoute()
    const router=useRouter()

    const {data, getData, loading, errorData}=useGetData()

    // const poke=ref({})
    const back=()=>{
        router.push('/pokemons')
    }
    // const getData=async()=>{
    //     try {
    //         const {data}=await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
    //         poke.value=data
    //         console.log(data);            
    //     } catch (error) {
    //         console.log(error);
    //         poke.value=null
    //     }
    // }
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>
<template>
    <div v-if="loading">Cargando...</div>
    <div v-if="errorData" class="alert alert-danger">No existe el pokemon</div>
    <div v-if="data">
        <img :src="data.sprites?.front_default" alt="">
        <h1>pokemon name: {{ $route.params.name }}</h1>
    </div>
    <button class="btn btn-secondary" @click="back">back</button>
</template>