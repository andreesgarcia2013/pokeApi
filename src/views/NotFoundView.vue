<script setup>
import {useRouter} from "vue-router";
const router=useRouter()
const back=()=>{
    router.push('/pokemons')
}
</script>
<template>
    <button class="btn btn-outline-secondary" @click="back">back</button>
    <h1>404</h1>
</template>