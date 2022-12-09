<template>
  <v-app id="app">
    <v-container fluid class="px-0 py-0">
      <NavMenu />
    </v-container>
    <!-- <nav-menu /> -->
    <v-main>
      <v-container fluid class="px-0 py-0">
        <router-view />
      </v-container>
    </v-main>
    
    <footer>
      <v-container fluid class="px-0 py-0">
        <Footer />
      </v-container>
    </footer>

  </v-app>
</template>

<script>
import Footer from './components/Footer.vue';
import NavMenu from './components/NavMenu.vue';

export default {
  components: { NavMenu, Footer },
  name: 'App',

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
#app {
  background: url('../public/img/'+$background_image) $background-repeat $background-position;
  background-size: cover;

  color: $color_main-lightest;
  font-family: $font-family-text;

  h1{
    font-family: $font-family_titles;
    font-size: $font-size_titles;
  }

  p{
    font-family: $font-family-text;
    font-size: $font-size_text;
  }
}
</style>