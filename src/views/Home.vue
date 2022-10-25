<template>
  <main v-if="API_responses">

    <!-- <div class="API_card" v-for="(res, index) in API_responses" :key="index">
      <h1>{{ res.name }}</h1>
      <img :src="res.thumbnail.path + '.' + res.thumbnail.extension" />
    </div> -->
    <h1>Home</h1>

  </main>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',

  data() {
    return {
      // test: 'Initial value',
      
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
    // this.test = import.meta.env.VITE_TEST_ENV;
    this.API_publicKey = import.meta.env.VITE_API_PUBLIC_KEY;
    this.API_ts = import.meta.env.VITE_API_TS;
    this.API_hash = import.meta.env.VITE_API_HASH;
    this.API_url = `${import.meta.env.VITE_API_BASE_URL}v1/public`;

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
    
  }
}
</script>

<style lang="scss" scoped>

</style>
