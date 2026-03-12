<script setup>
import { computed, ref } from "vue";
import { vConfetti } from "@neoconfetti/vue";

defineProps({
  questions: Array,
});
const count = ref(0);
const isClicked = ref(false);
const showQuestions = ref(false);

const popThumbUp = computed(() => count.value++);
const popThumbDown = computed(() => (count.value += 0));

function handleClick() {
  isClicked.value = true;
  count.value = 0;
}
</script>

<template>
  <ul>
    <li v-for="question in questions" :key="question">
      {{ question }}
      <div class="answers">
        <button class="answer up" @click.prevent="popThumbUp">👍</button>
        <button class="answer down" @click.prevent="popThumbDown">👎</button>
      </div>
    </li>
  </ul>
  <button class="show-result" @click="handleClick">Calculer mes résultats</button>
  <h2 v-if="isClicked">
    Félicitations ! {{ count }} / {{ questions.length }} services que vous utilisez sont basés aux
    USA !
  </h2>
  <div class="confettis" v-if="isClicked" v-confetti></div>
</template>

<style>
li {
  display: flex;
  align-items: center;
  gap: 10px;
}

.answers {
  display: flex;
  gap: 5px;
}

.answer {
  position: relative;
  border: none;
  background: transparent;
  cursor: pointer;
  padding: 0;
}

span {
  position: absolute;
  transition: bottom 1s ease-in-out;
  top: 0;
  left: 0;
  opacity: 20%;
}
</style>
