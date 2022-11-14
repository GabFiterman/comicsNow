<template>
  <v-app id="app">
    <!-- <nav-menu /> -->
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import NavMenu from './components/NavMenu.vue';

export default {
  components: { NavMenu },
  name: 'App',

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
#app {
  background: url('../public/img/ComicsBackground.png')repeat 0 0 fixed;
  background-size: cover;

  color: $test;
}
</style>