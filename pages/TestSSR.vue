<script setup lang="ts">
const { data } = await useFetch('/api/hello')

const countOnClient = ref(0);
const countOnServer = ref(0);

function incrementClientCount() {
    countOnClient.value += 1
}
function incrementServerCount() {
    countOnServer.value += 1
}

</script>

<script lang="ts">
</script>


<template>

    <h1>Testing SSR</h1>

    This should show with or without JS {{ incrementServerCount() }}.
    <!-- <button onclick="incrementServerCount()" /> -->

    <!-- <ClientOnly>
        This is from the client only! {{ incrementClientCount()  }}
    </ClientOnly> -->

</template>
