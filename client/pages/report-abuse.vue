<template>
  <div class="max-w-2xl mx-auto px-4 py-12">
    <h1 class="text-2xl font-semibold text-neutral-900 dark:text-white mb-4">
      Report abuse
    </h1>
    <p class="text-neutral-600 dark:text-neutral-400">
      For this Afintrix deployment, contact your workspace administrator or hosting operator to report abuse.
    </p>
    <open-form-footer />
  </div>
</template>

<script setup>
useOpnSeoMeta({
  title: "Report Abuse",
})
definePageMeta({
  middleware: ["self-hosted"]
})
defineRouteRules({
  swr: 3600,
})
</script>
