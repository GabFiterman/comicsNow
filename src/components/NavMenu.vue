<template>
  <v-container fluid>
    <v-row class="navMenu">

      <v-col cols="1">
        <FloatMenu />
      </v-col>

      <v-col cols="11">
        <!-- Logo + MainIcons  -->
        <v-row v-if="searching" align="center" justify="space-between" class="ml-4">
          <v-toolbar-title>
            <router-link to="/">
              <v-img class="logo" src="../../public/Marvel-Comics-Logo.png"></v-img>
            </router-link>
          </v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn-toggle :v-model="2">
            <v-btn @click="toggleSearching" icon color="white">
              <v-icon>mdi-magnify</v-icon>
            </v-btn>

            <router-link to="/CustomEvents">
              <v-btn icon color="white">
                <v-icon>mdi-heart</v-icon>
              </v-btn>
            </router-link>

            <v-btn icon color="white">
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-btn-toggle>
        </v-row>

        <!-- Searching Area -->
        <v-row v-else class="navMenu__search">
          <v-col cols="10">
              <SearchBox />
          </v-col>

          <v-col cols="2">
            <v-btn-toggle :v-model="2">
              <v-icon @click="toggleSearching" class="navMenu__search-icon">mdi-magnify</v-icon>
            </v-btn-toggle>
          </v-col>

        </v-row>
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
import SearchBox from './SearchBox.vue';
import FloatMenu from './FloatMenu.vue';

export default {
  name: "NavMenu",

  data: () => ({
    bars: [
      { class: '' },
      { class: '', dark: true },
      { class: 'primary', dark: true },
      { class: 'elevation-0' },
    ],
    searching: false,
  }),

  methods: {
    toggleSearching() {
      this.searching = !this.searching;
    },
  },

  components: {
    SearchBox,
    FloatMenu
  }
}
</script>

<style lang="scss" scoped>
.logo {
  height: 3.5rem;
  width: 7.5rem;
  opacity: .75;
  border-radius: 6px;
}

.navMenu {
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(6.9px);
  -webkit-backdrop-filter: blur(6.9px);
  border: 1px solid rgba(255, 255, 255, 0.37);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 15vh;

  .navMenu__search {
    display: flex;
    align-items: center;

    .navMenu__search-icon{
      padding: .25rem;
    }
    
  }
}
</style>