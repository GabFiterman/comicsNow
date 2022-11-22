<template>
  <v-container fluid>
    
    <v-app-bar fixed elevate-on-scroll scroll-target="#scrolling-techniques-7">
      <v-menu transition="slide-x-transition" bottom right>
        <template v-slot:activator="{ on, attrs }">
          <div v-bind="attrs" v-on="on">
            <v-app-bar-nav-icon color="white"></v-app-bar-nav-icon>
          </div>

        </template>

        <v-list>
          <v-list-item v-for="(item, i) in items" :key="i">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <!-- <v-spacer></v-spacer> -->
      <v-toolbar-title>
        <v-img v-if="!searching" class="logo" src="../../public/Marvel-Comics-Logo.png"></v-img>
        <SearchBox v-else />
      </v-toolbar-title>
      
      <v-spacer v-if="!searching"></v-spacer>

      <v-btn icon color="white">
        <v-icon @click="toggleSearching">mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon color="white" v-if="!searching">
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon color="white" v-if="!searching">
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

    </v-app-bar>
  </v-container>
</template>

<script>
import SearchBox from './SearchBox.vue';

export default {
  name: "NavMenu",
  data: () => ({
    items: [
      { title: "Click Me" },
      { title: "Click Me" },
      { title: "Click Me" },
      { title: "Click Me 2" },
    ],
    searching: false,
  }),
  methods: {
    toggleSearching() {
      this.searching = !this.searching;
    }
  },
  components: { SearchBox }
}
</script>

<style lang="scss" scoped>
.logo {
  height: 3.5rem;
  width: 7.5rem;
  opacity: .75;
  border-radius: 6px;

}

.theme--light.v-app-bar.v-toolbar.v-sheet {
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(6.9px);
  -webkit-backdrop-filter: blur(6.9px);
  border: 1px solid rgba(255, 255, 255, 0.37);
  color: white;
}
</style>