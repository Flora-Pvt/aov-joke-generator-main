<template>
  <div class="w-full h-full flex justify-center items-center flex-col gap-y-4">
    <div class="text-3xl">{{ data.setup }}</div>
    <button @click="showDelivery = true" role="button" name="Tell Me!">Tell Me!</button>

    <div v-if="showDelivery" class="text-3xl">{{ data.delivery }}</div>
    <button v-if="showDelivery" @click="getJoke" role="button" name="Another">Another</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let data = ref({ setup: '', delivery: '' })
let showDelivery = ref(false)

const getJoke = async () => {
  showDelivery.value = false

  const res = await fetch('https://v2.jokeapi.dev/joke/christmas').catch(() => alert('An error has occured.'))
  data.value = res ? await res.json() : null
}

getJoke()
</script>
