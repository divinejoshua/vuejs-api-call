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
    //For AWS API Gateway to work, Delete the OPTIONS request from the method lists
    const response = await fetch('https://1k6dp49v7b.execute-api.us-east-1.amazonaws.com/teststage/about');
    const data = await response.json()
    info.value = data.body
    
  } catch (error) {
    console.error(error);
  }
}
</script>

<template>
  <div class="about">
    <h1>{{info}}</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
