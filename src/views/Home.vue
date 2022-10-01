<template>
  <main>
    <h1>{{ test }}</h1>
  </main>
</template>

<script>
  
export default {
  name: 'Home',
  data(){
    return {
      test: 'Initial value',
    };
  },
  created(){
    this.test = import.meta.env.VITE_TEST_ENV;
  }
}
</script>
