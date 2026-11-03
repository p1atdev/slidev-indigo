<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
import IndigoPoint from "../components/IndigoPoint.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <IndigoFrame class="three-cols" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber">
    <slot />
    <div class="indigo-three-columns">
      <IndigoPoint index="01" :accent="4"><slot name="left" /></IndigoPoint>
      <IndigoPoint index="02" :accent="6"><slot name="middle" /></IndigoPoint>
      <IndigoPoint index="03" :accent="8"><slot name="right" /></IndigoPoint>
    </div>
    <template v-if="$slots.note" #note><slot name="note" /></template>
  </IndigoFrame>
</template>
