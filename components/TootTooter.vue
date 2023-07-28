<script setup lang="ts">
import { API } from 'aws-amplify'

import { createToots } from '../graphql/mutations'
import { listToots } from '../graphql/queries'
import { asyncComputed } from '@vueuse/core'

import { ref } from 'vue'

async function sendToot() {
  try {
    const newToots: any = await API.graphql({
      query: createToots,
      variables: {
        input: {
          who_delt_it: 'Tom',
          notes: 'moist and resonant',
          data: '{}'
        }
      }
    })
    console.log(newToots)
    count.value = count.value + 1
  } catch (e) {
    console.error('failed saving post', e)
  }
}

async function getTootCount() {
  const toots = (await API.graphql({ query: listToots })) as any

  return toots.data.listToots.items.length
}

const name = ref('No one')
const evaluating = ref(false)

const allTootsCount = asyncComputed(
  getTootCount,
  null, // initial state,
  evaluating
)
const count = ref(allTootsCount)
</script>

<template>
  <v-card width="450">
    <v-card-title
      >Toot Ninja <img alt="toot... ninja..." src="@/assets/toot-ninja-outline.png" height="125" />
    </v-card-title>
    <v-card-text>{{ name }} tooted {{ count }} times</v-card-text>
    <v-text-field v-model="name" label="Name" placeholder="name" />
    <v-card-actions>
      <v-btn @click="sendToot" variant="text">toot?</v-btn>
    </v-card-actions>
  </v-card>
</template>

<style></style>
