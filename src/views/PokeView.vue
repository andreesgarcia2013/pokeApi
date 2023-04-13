import axios from 'axios';
<script setup>
    import axios from 'axios';
    import { useRoute, useRouter } from "vue-router";
import { ref } from 'vue';
    const route= useRoute()
    const router=useRouter()

    const poke=ref({})
    const back=()=>{
        router.push('/pokemons')
    }
    const getData=async()=>{
        try {
            const {data}=await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
            poke.value=data
            console.log(data);            
        } catch (error) {
            console.log(error);
            poke.value=null
        }
    }
getData();
</script>
<template>
    <div v-if="poke">
        <img :src="poke.sprites?.front_default" alt="">
        <h1>pokemon name: {{ $route.params.name }}</h1>
    </div>
    <h1 v-else>
        no existe el pokemon
    </h1>
    <button class="btn btn-secondary" @click="back">back</button>
</template>