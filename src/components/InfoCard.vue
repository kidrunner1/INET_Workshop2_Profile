<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>

<template>
  <div class="rounded-2xl border border-slate-700 bg-slate-800 p-6">
    <h2 class="mb-4 text-xl font-bold text-white">
      {{ title }}
    </h2>

    <slot />
  </div>
</template>