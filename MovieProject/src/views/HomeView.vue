<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import NavbarView from './NavbarView.vue';

</script>

<template>
  <div class="app-root" id="app-root">
    <NavbarView/>
      <main>
        <TheWelcome />
      </main>
  </div>
</template>
