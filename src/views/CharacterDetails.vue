<script setup>
import { onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

import useCharacters from '@/composables/useCharacters'

const route = useRoute()
const { fetchCharacter, currentCharacter } = useCharacters()

onMounted(async () => {
  await fetchCharacter(route.params.id)
  console.log(currentCharacter)
})

onUnmounted(() => {
  currentCharacter.value = null
})
console.log(currentCharacter)
</script>

<template>
  <main
    class="min-h-screen bg-gradient-to-r from-fuchsia-300 to-blue-400 py-8 text-white"
  >
    <div
      v-if="currentCharacter"
      class="flex flex-col items-center justify-center gap-6"
    >
      <img :src="currentCharacter.image" :alt="currentCharacter.name" />
      <h1 class="justify-content: center text-white-800 text-6xl font-bold">
        Hi, I'm {{ currentCharacter.name }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Location: {{ currentCharacter.location.name }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Origin: {{ currentCharacter.origin.name }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Species: {{ currentCharacter.species }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Gender: {{ currentCharacter.gender }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Status: {{ currentCharacter.status }}
      </h1>
      <h1 class="text-white-800 text-2xl font-bold">
        Type: {{ currentCharacter.type }}
      </h1>

      <pre></pre>
    </div>
  </main>
</template>
