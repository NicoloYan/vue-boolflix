<template>
    <main>
        <div v-if="arrayFilms == null">Cerca un Film</div>
        <div v-else>
        <h3>Films</h3>
        <div class="cards_container">
            <MovieCard
            v-for="element in arrayFilms"
            :key="element.id"
            :film-data="element"
            />
        </div>    
        <h3 class="series">Series</h3>
        <div class="cards_container">
            <SeriesCard
            v-for="element in arraySeries"
            :key="element.id"
            :serie-data="element"
            />
        </div>
        </div>
    </main>
</template>

<script>
import MovieCard from "./MovieCard.vue";
import SeriesCard from "./SeriesCard.vue";
export default {
    name: 'MainComponent',
    components: {
        MovieCard,
        SeriesCard
    },
    props: {
        arrayFilms: Array,
        arraySeries: Array,
    },
}
</script>

<style lang="scss" scoped>
main {
    background-color: #141414;
}
h3 {
    color: white;
    text-align: center;
    padding: 20px 0;
}
</style>