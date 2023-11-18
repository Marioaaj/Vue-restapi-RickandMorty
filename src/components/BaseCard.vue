<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable prettier/prettier -->
<script setup>
const props = defineProps({
  character: {
    type: Object,
    default: () => ({
      id: -1,
      name: 'Unknown',
      imageUrl: 'https://via.placeholder.com/150',
    }),
  },
})
</script>

<template>
  <RouterLink
    :to="`/character/${props.character.id}`"
    class="rounded-lg bg-lime-100 shadow-lg"
  >
    <img
      class="w-full rounded-t-lg object-cover"
      :src="props.character.image"
    />
    <div class="p-4">
      <h2 class="text-1xl font-semibold text-gray-800">
        {{ props.character.name }}
      </h2>
      <h2>{{ props.character.location.name }}</h2>
    </div>
  </RouterLink>
</template>
