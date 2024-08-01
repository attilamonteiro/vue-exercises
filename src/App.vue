<template>
  <h1>{{ first }} {{ last }}</h1>
  <UserName
    :first-name="first"
    :last-name="last"
    @update:first-name="first = $event"
    @update:last-name="last = $event"
  >
    <!-- Conteúdo adicional passado via slot -->
    <p>Additional content here.</p>
    <button @click="first = ''; last = ''">Clear</button>
  </UserName>
</template>

<script setup>
import { ref } from 'vue'
import UserName from './components/UserName.vue'

const first = ref('John')
const last = ref('Doe')
</script>


