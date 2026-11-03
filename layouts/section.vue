<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
withDefaults(
  defineProps<{
    eyebrow?: string;
    number?: string | number;
    footer?: string | false;
    pageNumber?: boolean;
  }>(),
  { footer: undefined, pageNumber: true },
);
</script>

<template>
  <IndigoFrame
    class="section"
    tone="light"
    :eyebrow="eyebrow"
    :footer="footer"
    :page-number="pageNumber"
  >
    <div class="indigo-section-copy"><slot /></div>
    <div v-if="number !== undefined" class="indigo-section-number" aria-hidden="true">
      {{ String(number).padStart(2, "0") }}
    </div>
  </IndigoFrame>
</template>
