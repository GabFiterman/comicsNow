<template>
  <div>
    <v-container id="home">
      <!-- Home Intro -->
      <h1>Comics Now</h1>
      <div class="homeDescription">
        <p>Welcome to Comics Now, here you can search for your favorite Marvel heroes, comics and series.</p>
        <p><span class="buttonLabel">Login</span> or <span class="buttonLabel">Register</span> to start searching your
          favorites Marvel's characters or comics</p>
      </div>
    </v-container>

    <!-- Card  -->
    <v-container v-if="API_responses">
      <CardShow :API_responses="API_responses" />
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import CardShow from '@/components/CardShow.vue';

export default {
  name: 'Home',

  components: {
    CardShow,
  },

  data() {
    return {
      API_publicKey: null,
      API_ts: null,
      API_hash: null,
      API_url: null,

      API_fetchType: null,
      API_fetchFilter: null,
      API_fetchParam: null,

      API_responses: null,
    };
  },

  created() {
    this.API_publicKey = process.env.VUE_APP_PUBLIC_KEY;
    this.API_ts = process.env.VUE_APP_TS;
    this.API_hash = process.env.VUE_APP_HASH;
    this.API_url = `${process.env.VUE_APP_BASE_URL}v1/public`;

    this.API_fetchType = 'characters';
    this.API_fetchFilter = 'nameStartsWith';
    this.API_fetchParam = 'Hulk'
  },

  mounted() {
    let fetchQuery = `${this.API_url}/${this.API_fetchType}?${this.API_fetchFilter}=${this.API_fetchParam}&ts=${this.API_ts}&apikey=${this.API_publicKey}&hash=${this.API_hash}`;

    axios
      .get(fetchQuery)
      .then((res) => {
        console.log(fetchQuery)
        this.API_responses = res.data.data.results;
        console.log('---------- API_responses: ');
        console.log(this.API_responses)
      })
      .catch((err) => {
        console.log(fetchQuery)
        console.error(err);
      });
  },

};
</script>

<style lang="scss" scoped>
#home {
  .homeDescription {
    max-width: 75vw;
    text-align: start;
  }

  .buttonLabel {
    background-color: $color_main-darkest;
    border: $border_main_width $border_main_line $color_main-lightest;
    border-radius: 2px;
    color: $color_main-lightest;
    font-weight: bold;
    padding: 0.25rem 0.45rem;

    transition: $transition_main;

    &:hover {
      filter: brightness(1.55);
      cursor: pointer;
    }
  }
}
</style>
