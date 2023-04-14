<script setup>
import { storeToRefs } from 'pinia';
import TheWelcome from '../components/TheWelcome.vue'
import {useCounterStore} from '@/store/counter.js'
const  useCounter=useCounterStore()

const {increment}=useCounter
const {count, double}=storeToRefs(useCounter)
</script>

<template>
  <h1>Home counter: {{count }}</h1>
  <h1>double counter: {{double }}</h1>
  <button @click="increment">Increment</button>

</template>
