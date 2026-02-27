<script setup>
defineProps({
  color: String,
});
</script>

<template>
  <svg viewBox="0 0 16 16" fill="none">
    <path
      d="
      M 4,2
      L 14,8
      L 4,14
    "
      :stroke="`${color ? color : '#fff'}`"
      stroke-width="1.5"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</template>
