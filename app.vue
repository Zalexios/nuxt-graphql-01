<template>
  <div>
    <h2>Starlink Launches</h2>

    <p>Fetched {{ data?.launches?.length || 0 }} launches</p>

    <p v-for="(entry, i) of data?.launches" :key="entry.id">
      {{ i + 1 }}. Mission Name: {{ entry.mission_name }} ({{
        entry.launch_year
      }})
    </p>
  </div>
</template>

<script lang="ts" setup>
const { data, error } = await useAsyncGql({
  operation: 'launches',
  variables: { limit: 8 },
})
</script>

<style>
:root {
  --bg-color: #000;
  --text-color: #FFF;
}

body, html {
  background-color: var(--bg-color, #000000);
  color: var(--text-color, #FFFFFF);
}
</style>