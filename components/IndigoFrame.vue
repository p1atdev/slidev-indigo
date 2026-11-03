<script setup lang="ts">
import { computed } from "vue";
import { useSlideContext } from "@slidev/client";

withDefaults(
  defineProps<{
    tone?: "light" | "dark";
    eyebrow?: string;
    footer?: string | false;
    pageNumber?: boolean;
  }>(),
  { tone: "light", footer: undefined, pageNumber: true },
);

const { $page, $slidev } = useSlideContext();
const configuredFooter = computed(() => $slidev.configs.themeConfig?.footer);
</script>

<template>
  <div
    class="slidev-layout indigo-frame"
    :class="[`indigo-${tone}`, { 'indigo-has-note': $slots.note }]"
  >
    <div v-if="eyebrow" class="indigo-eyebrow">{{ eyebrow }}</div>
    <div class="indigo-body"><slot /></div>
    <div v-if="$slots.note" class="indigo-note"><slot name="note" /></div>
    <footer class="indigo-footer">
      <span v-if="footer !== false">{{ footer ?? configuredFooter }}</span>
      <span v-if="pageNumber" class="indigo-page">{{ String($page).padStart(2, "0") }}</span>
    </footer>
  </div>
</template>
