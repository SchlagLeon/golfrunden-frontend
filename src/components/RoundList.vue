<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface Round {
  roundId: number
  date: string
  courseName: string
  note: string
}

const rounds = ref<Round[]>([])

function loadRounds() {
  const baseUrl = import.meta.env.VITE_BACKEND_BASE_URL
  const endpoint = baseUrl + '/api/rounds'
  const requestOptions: RequestInit = {
    method: 'GET',
    redirect: 'follow',
  }
  fetch(endpoint, requestOptions)
    .then((response) => response.json())
    .then((result: Round[]) => {
      rounds.value = result
    })
    .catch((error) => console.log('error', error))
}

onMounted(loadRounds)
</script>

<template>
  <h2>Meine Runden</h2>
  <ul>
    <li v-for="round in rounds" :key="round.roundId">
      {{ round.date }}: {{ round.courseName }} ({{ round.note }})
    </li>
  </ul>
</template>
