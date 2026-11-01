<script setup lang="ts">
import { ref } from 'vue'

interface Round {
  roundId: number
  date: string
  courseName: string
  note: string
}

const rounds = ref<Round[]>([
  { roundId: 1, date: '2026-10-11', courseName: 'Testplatz', note: 'Erste Testrunde' },
  { roundId: 2, date: '2026-10-18', courseName: 'Golfclub Beispiel', note: 'Windig' },
  { roundId: 3, date: '2026-10-25', courseName: 'Testplatz', note: 'Neue Bestleistung' },
])
</script>

<template>
  <h2>Meine Runden</h2>
  <ul>
    <li v-for="round in rounds" :key="round.roundId">
      {{ round.date }}: {{ round.courseName }} ({{ round.note }})
    </li>
  </ul>
</template>
