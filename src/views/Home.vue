<template>
  <!-- <div class="home">

    <div v-for="(res, index) in API_responses" :key="index">
      <h1>
        {{res.name}}
      </h1>
      <ul>
        <li v-for="(event, index) in res.events.items" :key="index">{{event.name}}</li>
      </ul>
    </div>
  </div> -->
  <v-container>
    <h1>Comics Now</h1>
    <div class="homeDescription">
      <p>Welcome to Comics Now, here you can search for your favorite Marvel heroes, comics and series.</p>
      <p><span class="buttonLabel">Login</span> or <span class="buttonLabel">Register</span> to start searching your
        favorites Marvel's characters or comics</p>
    </div>
  </v-container>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'Home',

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
    this.API_fetchParam = 'Black'
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
.container {
  margin: 5vh 5vw;
  .homeDescription{
    max-width: 75vw;
    text-align:start;
  }
  .buttonLabel {
    background-color: $color_main-darkest;
    border: 1px solid $color_main-lightest;
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
