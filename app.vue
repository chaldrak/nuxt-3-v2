<template>
  <div>
    <NuxtPage />  
  </div>
</template>
<script setup>
const route = useRoute()

useHead({
  title: 'My App',
  // or, instead:
  // titleTemplate: (title) => `My App - ${title}`,
  viewport: 'width=device-width, initial-scale=1, maximum-scale=1',
  charset: 'utf-8',
  meta: [
    { name: 'description', content: 'My amazing site.' },
    { name: 'og:title', content: `App Name - ${route.meta?.title || "page"}` }
  ],
  bodyAttrs: {
    class: 'test'
  }
})
</script>
