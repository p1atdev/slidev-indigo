<script setup lang="ts">
defineProps<{ value: string; label?: string }>();
</script>

<template>
  <div class="indigo-metric">
    <p v-if="label" class="indigo-metric-label">{{ label }}</p>
    <div class="indigo-metric-value">{{ value }}</div>
    <div class="indigo-metric-rule" aria-hidden="true" />
    <div class="indigo-metric-copy"><slot /></div>
  </div>
</template>
