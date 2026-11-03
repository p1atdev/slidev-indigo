<script setup lang="ts">
import IndigoFrame from "../components/IndigoFrame.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <IndigoFrame class="quote" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber"
    ><slot
  /></IndigoFrame>
</template>
