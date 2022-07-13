<template>
    <main>
        <div v-if="arrayFilms == null">Cerca un Film</div>
        <div v-else>
        <h3>films</h3>
        <div>
            <MovieCard
            v-for="element in arrayFilms"
            :key="element.id"
            :film-data="element"
            />
            <h3 class="series">Series</h3>
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
.series {
    background-color: blue;
}
</style>