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

  <p
    v-if="afficheErreur"
    class="error"
  >
    Vous devez saisire qqch !!!
  </p>
  <input
    v-model="nouveauJeu"
    type="text"
  >
  <v-btn @click="ajouteJeu">
    Ajouter
  </v-btn>

  <ul>
    <li
      v-for="(leJeu, index) in jeux"
      :key="index"
    >
      {{ index }} - {{ leJeu }}
    </li>
  </ul>
</template>

<script setup>
// Importation de la fonction ref
import { ref } from 'vue'

// Variable pour le compteur
const count = ref(0)
// Variable pour le nouveau jeu
const nouveauJeu = ref('')
// Variable pour l'erreur
const afficheErreur = ref(false)
// Tableau de jeux
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

// Fonction qui ajouter le nouveau jeu
function ajouteJeu () {
  if(nouveauJeu.value === '') {
    afficheErreur.value = true
    return
  }

  afficheErreur.value = false
  jeux.value.push(nouveauJeu.value)
}
</script>

<style scoped lang="sass">
  /* Titre 1 */
  h1
    color: yellow

  .error
    color: darken(red, 20%)

  .valid
    color: green

  input
    background-color: aliceblue
    color: black
    padding: 4px 2px
</style>
