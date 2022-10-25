<template>
  <Menu />
  <RouterView />
</template>

<script>
import Menu from './components/Menu.vue'
export default {
  components: { Menu },
  name: 'App',
}
</script>

<style lang="scss">

body {
  margin: 0;
  padding: 0;
  background-image: url('../public/Main_Background.webp');
  background-repeat: repeat;
  background-size: cover;

  color: $color__text-main;


  font-family: $font__main;
  font-size: 16px;

  h1 {
    font-size: 2.5rem;
    font-family: $font__titles;
  }

  h2 {
    font-size: 2rem;
    font-family: $font__titles;
  }

  h3 {
    font-size: 1.5rem;
    font-family: $font__titles;
  }

  p {
    font-family: $font__main;
    font-size: 1rem;

    .sm {
      font-size: 0.75rem;
    }

    .xsm {
      font-size: 0.5rem;
    }
  }

  b,
  strong {
    font-weight: bold;
  }

}
</style>