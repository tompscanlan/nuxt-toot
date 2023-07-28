<script setup lang="ts">
const { data } = await useFetch('/api/hello')
</script>

<script lang="ts">
</script>

<template>

    <h1>Testing SSR, from the server side</h1>

    This should show from the Client: 
    <!-- <ClientOnly>
        this is from the client!
    </ClientOnly> -->

</template>
