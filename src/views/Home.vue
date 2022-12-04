<template>
  <v-col cols="12">
    <v-row id="home">
      <CardHero />
    </v-row>

    <!-- Card  -->
    <v-row v-if="API_responses">
      <CardShow :API_responses="API_responses" />
    </v-row>
  </v-col>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import CardShow from '@/components/CardShow.vue';
import CardHero from '@/components/CardHero.vue';

export default {
  name: 'Home',

  components: {
    CardShow,
    CardHero,
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
      // appName_Lettering: '../../public/ComicsNow_Lettering.png',
    };
  },

  created() {
    this.API_publicKey = process.env.VUE_APP_PUBLIC_KEY;
    this.API_ts = process.env.VUE_APP_TS;
    this.API_hash = process.env.VUE_APP_HASH;
    this.API_url = `${process.env.VUE_APP_BASE_URL}v1/public`;

    this.API_fetchType = 'characters';
    this.API_fetchFilter = 'nameStartsWith';
    this.API_fetchParam = 'Ni'
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
  
}
</style>
