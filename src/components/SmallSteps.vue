<script setup lang="ts">
import RightIcon from "../assets/RightIcon.vue";

defineProps<{
  text: string;
  logo: string;
  list: List[];
}>();

type List = {
  label: string;
  link: string;
  logo: string;
};
</script>

<template>
  <div class="list">
    <div class="item">
      <img class="logo" :src="logo" :alt="text" />
      <RightIcon color="#000" width="20" />
      <a v-for="item in list" :href="item.link" target="_blank" class="item-logo">
        <img class="item-logo" :src="item.logo" alt="" />
        <span class="sr-only">{{ item.label }}</span>
      </a>
    </div>
  </div>
</template>

<style>
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  overflow: hidden;
  clip-path: inset(50%);
  white-space: nowrap;
  border: 0;
}

.list {
  margin: 16px auto;
}

.item {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.item-logo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.item-logo {
  width: 80px;
  height: auto;
}

.logo {
  width: 80px;
  height: auto;
  filter: grayscale(1) brightness(1);
}
</style>
