<script setup lang="ts">
import RightIcon from "../assets/RightIcon.vue";

defineProps<{
  text: string;
  logo: string;
  list: List;
}>();

type List = {
  label: string;
  link: string;
};
</script>

<template>
  <h2>Par quoi remplacer les outils ?</h2>
  <div class="item">
    <img :src="logo" :alt="text" />
    <RightIcon color="#000" width="30" />
    <a v-for="item in { label, link }" :href="item.link">{{ item.label }}</a>
  </div>
</template>

<style>
.item {
  display: flex;
  align-items: center;
  gap: 1rem;
}
</style>
