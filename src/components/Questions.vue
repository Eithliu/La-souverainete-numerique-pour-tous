<script setup>
defineProps({
  questions: Array,
});

defineEmits(["like", "dislike"]);
</script>

<template>
  <li v-for="question in questions" :key="question">
    {{ question }}
    <div class="answers">
      <button class="answer" @click="$emit('like')">👍</button>
      <button class="answer" @click="$emit('dislike')">👎</button>
    </div>
  </li>
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
  border: none;
  background: transparent;
  cursor: pointer;
  padding: 0;
}
</style>
