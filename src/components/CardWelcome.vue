<template>
  <v-card class="card-hero mx-auto mb-10 mt-8">
        <v-img alt="Comics Now" src="../../public/ComicsNow_Lettering.png"></v-img>

        <v-card-subtitle class="card-text px-10 pb-5 mt-6">
          <p>{{ welcomeText }}</p>
          <br />
          <p>
            <v-btn class="card-button" rounded><router-link to="/">Login</router-link></v-btn>
            or 
            <v-btn class="card-button" rounded><router-link to="/">Register</router-link></v-btn>
            to start searching your favorites Marvel's characters or comics
          </p>

        </v-card-subtitle>
      </v-card>
</template>

<script>
export default {
    name: 'CardHero',

    data() {
      return {
        welcomeText: 'Welcome to Comics Now, here you can search for your favorite Marvel heroes, comics and series.',

      }
    }
}
</script>

<style lang="scss" scoped>
.card-hero {
    // glassmorphism: https://css.glass/
    background: rgba(255, 255, 255, 0.04);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(7.1px);
    -webkit-backdrop-filter: blur(7.1px);
    border: 1px solid rgba(255, 255, 255, 0.53);

    .card-text{
        p{
        font-size: 1.10rem !important;
        color: white;
        text-align: center;
        line-height: 2rem;
      }
    }

    .card-button{
      background-color: $color-main_darkest;
      transition: $transition_main;
      a{
        color: $color-main_lightest;
        text-decoration: none;
        font-weight: bold;
      }

      &:hover{
        filter: invert(1);
      }
    }

  }
</style>