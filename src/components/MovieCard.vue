<template>
    <div class="card">
        <div v-if="textVisibility === false">
            <div v-if="filmData.poster_path != null">
                <img
                @mouseenter="textVisibility = true"
                :src="'http://image.tmdb.org/t/p/w342/' + filmData.poster_path"
                :alt="filmData.title"
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
            <h3>Titolo: {{ filmData.title }}</h3>
            <h4
            v-show="
                filmData.title.toLowerCase() != filmData.original_title.toLowerCase()
            "
            >
            Titolo originale: {{ filmData.original_title }}
            </h4>
            <div>
                Lingua <lang-flag :iso="filmData.original_language" :squared="false" />
            </div>
            <h5>Overview: {{ filmData.overview }}</h5>
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
    name: 'MovieCard',
    data() {
        return {
            textVisibility: false,
            starf: "star",
            arrayStars: [],
            stars: Math.round(this.filmData.vote_average / 2),
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