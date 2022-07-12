<template>
  <div id="app">
    <HeaderComponent @ricercaFilm="funzioneRicercaFilm"/>
    <MainComponent :array-films="arrayFilms"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
  },
  data() {
    return {
      arrayFilms: null,
    }
  },
  methods: {
    funzioneRicercaFilm(arrayFilms) {
      this.arrayFilms = arrayFilms;
    },
  },
}
</script>

<style lang="scss">
// RESET
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
