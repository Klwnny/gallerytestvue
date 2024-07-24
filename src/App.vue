<script setup>
import DataSetup from './components/DataSetup.vue'
</script>

<template>
  <Suspense>
    <template #default>
      <DataSetup />
    </template>
    <template #fallback> Loading... </template>
  </Suspense>
</template>
