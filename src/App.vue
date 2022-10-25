<template>
  <RouterView />
</template>

<script>
export default {
  name: 'App',
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300;400;500;600;700&family=Righteous&display=swap');

$color__text-main: #FFD3D3;

$font__titles: 'Righteous', cursive;
$font__main: 'Comfortaa', cursive;

body {
  background-image: url('../public/Main_Background.webp');
  background-repeat: repeat;
  background-size: cover;

  color: #fafafa;

  
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

  b, strong {
    font-weight: bold;
  }

}
</style>