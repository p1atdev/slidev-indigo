<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <IndigoFrame class="data" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber">
    <slot />
    <div class="indigo-data-columns">
      <div class="indigo-data-chart"><slot name="chart" /></div>
      <aside class="indigo-data-metric"><slot name="metric" /></aside>
    </div>
    <template v-if="$slots.note" #note><slot name="note" /></template>
  </IndigoFrame>
</template>
