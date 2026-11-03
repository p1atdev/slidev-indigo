<script setup lang="ts">
import { computed } from "vue";

interface BarItem {
  label: string;
  value: number;
  color: 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8;
}

const props = withDefaults(
  defineProps<{
    title: string;
    items: BarItem[];
    max?: number;
    unit?: string;
  }>(),
  { max: 100, unit: "%" },
);

const bars = computed(() => {
  if (!Number.isFinite(props.max) || props.max <= 0)
    throw new Error("IndigoBarChart: max must be a finite positive number.");
  return props.items.map((item) => {
    if (!Number.isFinite(item.value) || item.value < 0 || item.value > props.max)
      throw new Error(
        `IndigoBarChart: ${item.label} must have a value between 0 and ${props.max}.`,
      );
    return { ...item, width: `${(item.value / props.max) * 100}%` };
  });
});
</script>

<template>
  <figure class="indigo-chart" :aria-label="title">
    <figcaption class="indigo-chart-title">{{ title }}</figcaption>
    <div v-for="(item, i) in bars" :key="i" class="indigo-chart-row">
      <span class="indigo-chart-label">{{ item.label }}</span>
      <div class="indigo-chart-track" aria-hidden="true">
        <div
          class="indigo-chart-fill"
          :style="{ width: item.width, background: `var(--color-${item.color})` }"
        />
      </div>
      <span class="indigo-chart-value">{{ item.value }}{{ unit }}</span>
    </div>
  </figure>
</template>
