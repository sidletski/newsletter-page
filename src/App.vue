<template>
  <div id="app">
    <app-header/>
    <router-view/>
  </div>
</template>

<script>
import Header from '@/components/Header'

export default {
  name: 'App',
  components: {
    'app-header': Header,
  }
}
</script>

<style lang="scss">
@import './assets/styles/vars.scss';
@import './assets/styles/reset.scss';
@import './assets/styles/fonts.scss';
@import './assets/styles/main.scss';

#app {
  font-family: "Geomanist", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
