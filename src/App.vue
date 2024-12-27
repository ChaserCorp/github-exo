<template>
  <div id="app">
    <Navbar />
    <router-view />
    <Footer />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';

export default defineComponent({
  name: 'App',
  components: {
    Navbar,
    Footer,
  },
});
</script>

<style>

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

#app > * {
  flex-shrink: 0;
}

#app > .router-view {
  flex-grow: 1;
}
</style>