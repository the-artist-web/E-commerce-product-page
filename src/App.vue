<template>
  <Header />
  <main>
    <article>
      <Hero />
    </article>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Header from '@/views/Header.vue'
import Hero from '@/views/Hero.vue'

export default defineComponent({
  name: 'App',
  components: {
    Header,
    Hero
  }
});
</script>

<style>
#app {
  height: auto;
  width: 100%;
  display: flex;
  flex-direction: column;
}
</style>
