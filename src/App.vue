<script setup lang="ts">
import { computed, ref } from "vue";
import Questions from "./components/Questions.vue";
import Why from "./components/Why.vue";
import SmallSteps from "./components/SmallSteps.vue";

const count = ref(0);
const showPage = ref<Page>(undefined);

type Page = "quiz" | "choices" | "small-steps" | "my-small-steps";

const quizPageShown = usePageShown("quiz");
const choicesPageShown = usePageShown("choices");
const smallStepsPageShown = usePageShown("small-steps");
const mySmallStepsPageShown = usePageShown("my-small-steps");

function usePageShown(page: Page) {
  return computed({
    get: () => showPage.value === page,
    set() {
      showPage.value = page;
    },
  });
}

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
    <nav>
      <ul class="navigation-menu">
        <li>
          <button @click="quizPageShown = true">Quiz</button>
        </li>
        <li>
          <button @click="choicesPageShown = true">Pourquoi</button>
        </li>
        <li>
          <button @click="smallStepsPageShown = true">Les petits pas</button>
        </li>
        <li>
          <button @click="mySmallStepsPageShown = true">Mes petits pas</button>
        </li>
      </ul>
    </nav>
    <h1>La souveraineté numérique chez soi</h1>
    <h2>La MeJ qui te fait reprendre la main sur tes données</h2>
    <Questions :questions v-if="quizPageShown" @like="count++" @dislike="" />
    <Why v-if="choicesPageShown" />
    <SmallSteps text="Google Chrome" logo="./assets/google.png" />
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

nav {
  display: flex;
}

.navigation-menu {
  display: flex;
  align-items: center;
  gap: 1rem;
}

button {
  border: none;
  background: transparent;
  cursor: pointer;
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

.show-result {
  padding: 0.8rem 1.5rem;
  border: none;
  background: #5e6c84;
  color: #fff;
  border-radius: 5px;
  width: fit-content;
  margin: auto;
  cursor: pointer;
}

.navigation {
  display: flex;
  justify-content: flex-end;
}

.icon {
  width: 40px;
  cursor: pointer;
}
</style>
