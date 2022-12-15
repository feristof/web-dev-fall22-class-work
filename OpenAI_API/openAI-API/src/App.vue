<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'

// using openai library
import { Configuration, OpenAIApi } from 'openai'

async function Apikey(){
  const configuration = new Configuration({
    apiKey: import.meta.env.VITE.Open_AI_Key,
  })
  const openai = new OpenAIApi(configuration);
  
  async function generateTxt( ) {
    const response = await openai.createCompletion({
      model: "text-davinci-003",
  prompt: "Say this is a test",
  temperature: 0,
  max_tokens: 20,
})
console.log(response.data.choices[0].text)
return response?.data.choices[0].text?.trim();
}

}



</script>

<template>
  <header>
    <div class="wrapper">
      <h1>OpenAI API</h1>
      </div>
<div>
  <!-- generate response -->
  <button @click="">Generate</button>

</div>

  </header>
  <main>
    
  </main>

  <RouterView />
</template>

<style scoped>

</style>
