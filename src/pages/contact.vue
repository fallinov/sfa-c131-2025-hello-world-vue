<template>
  <h1>Contact</h1>

  <p>Bonjour {{ nom }}</p>
  <v-btn>test</v-btn>
</template>

<script setup>
  import { ref } from 'vue'

  let nom = ref("Steve")
</script>

<style scoped>
* {
  border: 2px solid red;
}
</style>
