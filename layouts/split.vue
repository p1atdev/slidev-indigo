<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <IndigoFrame class="split" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber">
    <slot />
    <div class="indigo-split-columns">
      <div class="indigo-split-left"><slot name="left" /></div>
      <div class="indigo-split-right"><slot name="right" /></div>
    </div>
    <template v-if="$slots.note" #note><slot name="note" /></template>
  </IndigoFrame>
</template>
