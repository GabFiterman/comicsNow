<template>
  <v-app id="app">
    <v-container fluid>
      <NavMenu />
    </v-container>
    <!-- <nav-menu /> -->
    <v-main>
      <v-container fluid>
        <router-view />
      </v-container>
    </v-main>
    
    <div class="footer-container">
      <v-container fluid>
        <Footer />
      </v-container>
    </div>

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

  .footer-container{
    .container {
      padding: 0;
    }
  }
}
</style>