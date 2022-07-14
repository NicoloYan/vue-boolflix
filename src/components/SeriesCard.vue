<template>
  <div class="card">
    <div v-if="textVisibility === false">
            <div v-if="serieData.poster_path != null">
                <img
                @mouseenter="textVisibility = true"
                :src="'http://image.tmdb.org/t/p/w342/' + serieData.poster_path"
                :alt="serieData.title"
                >
            </div>
            <div v-else>
                <img 
                @mouseenter="textVisibility = true"
                src="https://www.electiondataservices.com/wp-content/uploads/2014/10/sorry-image-not-available.jpg"
                alt="placeholder">
            </div>
        </div>
    <div class="info_container" v-else @mouseleave="textVisibility = false">
      <h3>Titolo: {{ serieData.name }}</h3>
      <h4
        v-show="
          serieData.name.toLowerCase() != serieData.original_name.toLowerCase()
        "
      >
      Titolo originale: {{ serieData.original_name }}
      </h4>
      <div>
        Lingua <lang-flag
        :iso="serieData.original_language"
        :squared="false"
      />
      </div>
      <h5>Overview:{{ serieData.overview }}</h5>
      <div class="star_container">
        <div class="star" v-for="element in fullArrayStars()" :key="element">
          &starf;
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "MovieCard",
  data() {
    return {
      textVisibility: false,
      starf: "star",
      arrayStars: [],
      stars: Math.floor(this.serieData.vote_average / 2),
    };
  }, 
  components: {
    LangFlag,
  },
  props: {
    serieData: Object,
  },
   methods: {
    fullArrayStars() {
      console.log(this.stars);
      return this.stars;
    },
  },
};
</script>

<style scoped lang="scss">

</style>