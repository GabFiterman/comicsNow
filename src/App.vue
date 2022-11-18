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