<template>
    <div>
        <img
        v-show="filmData.poster_path != null"
        :src="'http://image.tmdb.org/t/p/w342/' + filmData.poster_path"
        :alt="filmData.title"
        />
        <h2>{{ filmData.title }}</h2>
        <h3
        v-show="
            filmData.title.toLowerCase() != filmData.original_title.toLowerCase()
        "
        >
        {{ filmData.original_title }}
        </h3>
        <lang-flag :iso="filmData.original_language" :squared="false" />
        <h4>{{ filmData.vote_average }}</h4>
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
    name: 'MovieCard',
    data() {
        return {
            starf: "star",
            arrayStars: [],
            stars: Math.floor(this.filmData.vote_average / 2),
        };
    },
    components: {
        LangFlag,
    },
    props: {
        filmData: Object,
    },
    methods: {
        fullArrayStars() {
            return this.stars;
        },
    },
}
</script>

<style lang="scss" scoped>

</style>