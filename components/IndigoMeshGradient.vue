<script setup lang="ts">
import { computed } from "vue";

const props = withDefaults(defineProps<{ seed?: string | number }>(), { seed: 42 });

const backgroundImage = computed(() => {
  const seed = props.seed;
  if (
    !(
      (typeof seed === "string" && seed.trim().length > 0) ||
      (typeof seed === "number" && Number.isFinite(seed))
    )
  )
    throw new Error("IndigoMeshGradient: seed must be a non-empty string or a finite number.");

  // Hash the seed, then use Mulberry32 so rendering never depends on Math.random().
  let state = 2166136261;
  for (const character of String(seed))
    state = Math.imul(state ^ character.codePointAt(0)!, 16777619);

  const random = () => {
    state = (state + 0x6d2b79f5) | 0;
    let value = Math.imul(state ^ (state >>> 15), 1 | state);
    value ^= value + Math.imul(value ^ (value >>> 7), 61 | value);
    return ((value ^ (value >>> 14)) >>> 0) / 4294967296;
  };

  const colors = [
    // 1,
    2, 3,
    // 4,
    5, 6,
    // 7,
    8,
  ];
  for (let i = colors.length - 1; i > 0; i--) {
    const j = Math.floor(random() * (i + 1));
    [colors[i], colors[j]] = [colors[j], colors[i]];
  }

  return colors
    .map((color, i) => {
      const x = (i % 2) * 60 + 20 + (random() - 0.5) * 44;
      const y = Math.floor(i / 2) * 30 + 5 + (random() - 0.5) * 30;
      const width = 62 + random() * 25;
      const height = 38 + random() * 15;
      return `radial-gradient(ellipse ${width.toFixed(2)}% ${height.toFixed(2)}% at ${x.toFixed(2)}% ${y.toFixed(2)}%, var(--color-${color}) 0%, transparent 100%)`;
    })
    .join(", ");
});

// const bgImage = `url("data:image/svg+xml,%3Csvg viewBox='0 0 1746 1746' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E"),radial-gradient(circle at 0% 99%, hsla(11,100%,50%,1) 0%, transparent 67%),radial-gradient(circle at 46% 94%, hsla(177,100%,50%,1) 0%, transparent 81%),radial-gradient(circle at 89% 8%, hsla(304,100%,9%,1) 0%, transparent 150%),radial-gradient(circle at 89% 8%, hsla(206,100%,9%,1) 0%, transparent 150%),radial-gradient(circle at 93% 95%, hsla(236,100%,23%,1) 0%, transparent 66%),radial-gradient(circle at 89% 8%, hsla(0,100%,99%,1) 0%, transparent 150%),radial-gradient(circle at 89% 8%, hsla(55,94%,54%,1) 0%, transparent 150%)`
</script>

<template>
  <div class="indigo-mesh-gradient" :style="{ backgroundImage }" aria-hidden="true" />

  <!-- <div 
   :style="{
	backgroundColor:`hsla(359,100%,50%,1)`,
	backgroundImage: bgImage,
	backgroundBlendMode:`overlay,normal,normal,normal,normal,normal,normal,normal`
}"
/> -->
</template>
