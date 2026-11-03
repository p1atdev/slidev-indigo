<script setup lang="ts">
import Cover from "./cover.vue";
withDefaults(defineProps<{ eyebrow?: string; footer?: string | false; pageNumber?: boolean }>(), {
  footer: undefined,
  pageNumber: true,
});
</script>

<template>
  <Cover :palette="false" :eyebrow="eyebrow" :footer="footer" :page-number="pageNumber"
    ><slot
  /></Cover>
</template>
