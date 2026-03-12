<script setup lang="ts">
defineProps<{
  title: string;
  content: string;
}>();

const choiceShown = defineModel<boolean>("choiceShown", { required: true });
</script>

<template>
  <div class="list-item">
    <li class="choice-item">
      <button @click="choiceShown = true">{{ title }}</button>
    </li>
    <p v-if="choiceShown">-> {{ content }}</p>
  </div>
</template>

<style>
.list-item {
  display: flex;
  gap: 1rem;
}

p {
  font-size: 18px;
}
</style>
