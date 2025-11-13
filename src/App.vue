<template>
  <ContactForm/>
</template>

<script setup lang="ts">
import ContactForm from './components/ContactForm.vue';

</script>

<style lang="scss">
:global(body) {
  background-color: #f0f2f5;
  margin: 0;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  color: #333;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
