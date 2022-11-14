<template>
   <v-app>
    <!-- <nav-menu /> -->
    <v-main>
      <router-view/>
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
