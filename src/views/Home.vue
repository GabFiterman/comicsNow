<template>
  <div class="home">
    <div v-for="(res, index) in API_responses" :key="index">
      <h1>
        {{res.name}}
      </h1>
      <ul>
        <li v-for="(event, index) in res.events.items" :key="index">{{event.name}}</li>
      </ul>
    </div>
  </div>
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

</style>
