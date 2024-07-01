<script setup lang="ts">

//@ts-ignore
import { onMounted, ref } from 'vue'


const info = ref("")


onMounted(() => {
  console.log(`the component is now mounted.`)
  fetchJokes()
})

async function fetchJokes() {
  try {
    const response = await fetch('https://1k6dp49v7b.execute-api.us-east-1.amazonaws.com/teststage/data');
    const data = await response.json()
    info.value = data.body
    
  } catch (error) {
    console.error(error);
  }
}
</script>

<template>
  <main>
    {{info}}
  </main>
</template>
