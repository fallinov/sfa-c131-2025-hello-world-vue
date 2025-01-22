<template>
  <p :class="{ error: count < 0, valid: count > 0 }">
    Compteur : {{ count }}
  </p>

  <p v-if="count > 9">
    Bravo tu à cliqué 10x !!!
  </p>

  <p v-else>
    Clique 10x pour voir...
  </p>

  <!-- Bouton -->
  <v-btn @click="increment">
    Incrémenter
  </v-btn>

  <v-btn
    class="ml-4"
    @click="decrement"
  >
    Décrémenter
  </v-btn>

  <hr>

  <ul>
    <li
      v-for="leJeu in jeux"
      :key="leJeu"
    >
      {{ leJeu }}
    </li>
  </ul>
</template>

<script setup>
// Importation de la fonction ref
import { ref } from 'vue'

let count = ref(0)
const jeux = ref([
  'Monopoly',
  'La Bonne Paye',
  'Scrabble',
  'Pictionary'
])
// Fonction qui incrémente count
function increment () {
  count.value++
}

// Fonction qui décrémente count
const decrement = () => count.value--

</script>

<style>
  /* Titre 1 */
  h1 {
    color: yellow;
  }

  .error {
    color: red;
  }

  .valid {
    color: green;
  }
</style>
