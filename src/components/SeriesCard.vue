<template>
  <div>
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
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "MovieCard",
  components: {
    LangFlag,
  },
  props: {
    serieData: Object,
  },
};
</script>

<style scoped lang="scss">

</style>