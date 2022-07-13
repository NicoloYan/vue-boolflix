<template>
  <div id="app">
    <HeaderComponent @ricercaFilm="funzioneRicercaFilm" @ricercaSerie="funzioneRicercaSerie"/>
    <MainComponent :array-films="arrayFilms" :array-series="arraySeries"/>
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
      arraySeries: null,
    }
  },
  methods: {
    funzioneRicercaFilm(arrayFilms) {
      this.arrayFilms = arrayFilms;
    },
    funzioneRicercaSerie(arraySeries) {
      this.arraySeries = arraySeries;
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
