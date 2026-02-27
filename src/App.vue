<script setup>
import { computed, ref } from "vue";
import Questions from "./components/Questions.vue";

const showQuestions = ref(false);
const count = ref(0);
const allQuestionsCount = ref(0);

const questions = [
  "J'utilise Google Chrome",
  "J'utilise un compte Gmail/YouTube",
  "J'utilise Notion ou OneNote ou Google Docs",
  "J'ai un compte sur l'un de ces réseaux: Facebook, Instagram, Twitter, Snapchat, WhatsApp",
  "J'ai un ordinateur (principal) sous Windows ou MacOS",
  "J'ai une carte Visa ou Mastercard",
];
</script>

<template>
  <header>
    <title>La souveraineté numérique chez soi</title>
  </header>
  <main>
    <h1>La souveraineté numérique chez soi</h1>
    <h2>La MeJ qui te fait reprendre la main sur tes données</h2>
    <button v-if="!showQuestions" @click.prevent="showQuestions = true">
      Mais d'abord, un petit Quiz !
    </button>
    <ul>
      <Questions :questions v-if="showQuestions" @like="count++" @dislike="count--" />
    </ul>
    {{ count }}
  </main>
</template>

<style>
* {
  font-family: "Roboto", "Arial", sans-serif;
  font-size: 16px;
  color: rgb(86 86 92);
}

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 15px;
}

li:not(:last-child) {
  margin-bottom: 10px;
}

h1,
h2 {
  text-align: center;
}

h1 {
  padding: 1rem;
  font-size: 24px;
}

h2 {
  padding: 0.8rem;
  font-size: 20px;
}

button {
  padding: 0.8rem 1.5rem;
  border: none;
  background: #5e6c84;
  color: #fff;
  border-radius: 5px;
  width: fit-content;
  margin: auto;
}
</style>
