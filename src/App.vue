<template>
  <div id="app">
    <header>
      <navbar/>
    </header>
    <section>
      <router-view/>
    </section>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';

export default {
  name: 'App',
  components: {
    Navbar,
  },
};
</script>

<style scoped>
header {
  margin-bottom: 20px;
}
</style>
