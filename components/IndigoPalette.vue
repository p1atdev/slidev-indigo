<script setup lang="ts">
const roles = ["BASE", "TITLE", "DEPTH", "RULE", "GRAPH", "ACCENT", "SUB", "HIGHLIGHT"];
withDefaults(defineProps<{ bars?: boolean }>(), { bars: false });
</script>

<template>
  <div
    :class="bars ? 'indigo-palette-bars' : 'indigo-palette'"
    :aria-hidden="bars ? true : undefined"
    :aria-label="bars ? undefined : '8色のカラーパレット'"
  >
    <div v-for="(role, i) in roles" :key="role" class="indigo-palette-item">
      <div class="indigo-swatch" :style="{ background: `var(--color-${i + 1})` }" />
      <template v-if="!bars">
        <span class="indigo-palette-role">{{ String(i + 1).padStart(2, "0") }} {{ role }}</span>
        <code class="indigo-palette-token">--color-{{ i + 1 }}</code>
      </template>
    </div>
  </div>
</template>
