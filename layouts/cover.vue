<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
import IndigoMeshGradient from "../components/IndigoMeshGradient.vue";
withDefaults(
  defineProps<{
    eyebrow?: string;
    footer?: string | false;
    pageNumber?: boolean;
    palette?: boolean;
    seed?: string | number;
  }>(),
  { palette: true, seed: 42, footer: undefined, pageNumber: true },
);
</script>

<template>
  <IndigoFrame
    class="cover"
    tone="light"
    :eyebrow="eyebrow"
    :footer="footer"
    :page-number="pageNumber"
    :class="{ 'indigo-with-palette': palette }"
  >
    <div class="indigo-cover-copy"><slot /></div>
    <div v-if="palette" class="indigo-cover-art">
      <IndigoMeshGradient :seed="seed" />
    </div>
  </IndigoFrame>
</template>
