<template>
  <v-container>
    <recipes v-if="data" :game-data="data" />
  </v-container>
</template>

<script setup lang="ts">
  import { ref } from 'vue'
  import { DataInterface } from '@/interfaces/DataInterface'
  import { useGameDataStore } from '@/stores/game-data-store'
  import Recipes from '@/components/recipes/Recipes.vue'

  const data = ref<DataInterface | null>(null)

  // The route guard ensures that the game data is always loaded by the time it gets here.
  const gameDataStore = useGameDataStore()
  data.value = gameDataStore.getGameData()
</script>
