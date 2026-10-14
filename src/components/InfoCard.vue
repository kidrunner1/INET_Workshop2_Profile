<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>

<template>
  <article class="rounded-2xl border border-slate-800 bg-slate-900/50 p-6
           transition hover:border-slate-700">
    <h2 class="mb-5 text-lg font-semibold text-white">
      {{ title }}
    </h2>

    <div class="text-sm leading-6 text-slate-400">
      <slot />
    </div>
  </article>
</template>