<script setup lang="ts">
// const { data } = await useFetch('/api/hello')
</script>

<script lang="ts">
function getRandUpToMax(max: number) : number {
  const quote = Math.floor(Math.random() * max);
  console.log("get id max: ", max, " is quote ", quote)

  return quote
}
</script>

<template>
  <!-- <pre>{{ data }}</pre> -->

  <RandomQuote  :id="getRandUpToMax(99)"/>

  <RouterLink to="about">About</RouterLink>
</template>
