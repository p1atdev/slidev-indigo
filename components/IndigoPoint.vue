<script setup lang="ts">
withDefaults(defineProps<{ index: string; accent?: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 }>(), {
  accent: 6,
});
</script>

<template>
  <article class="indigo-point" :style="{ '--point-accent': `var(--color-${accent})` }">
    <div class="indigo-point-index">{{ index }}</div>
    <div class="indigo-point-body"><slot /></div>
  </article>
</template>
