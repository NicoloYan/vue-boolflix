<template>
  <div>
    <img
      v-show="serieData.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342/' + serieData.poster_path"
      :alt="serieData.title"
    />
    <h2>{{ serieData.name }}</h2>
    <h3
      v-show="
        serieData.name.toLowerCase() != serieData.original_name.toLowerCase()
      "
    >
      {{ serieData.original_name }}
    </h3>
    <lang-flag
      :iso="serieData.original_language"
      :squared="false"
    />
    <h4>{{ serieData.vote_average }}</h4>
    <div>
      <div v-for="element in fullArrayStars()" :key="element">
        &starf;
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