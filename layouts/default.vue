<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <IndigoFrame class="default" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber">
    <slot />
    <template v-if="$slots.note" #note><slot name="note" /></template>
  </IndigoFrame>
</template>
