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
        </div>
        </div>
    </main>
</template>

<script>
import MovieCard from "./MovieCard.vue";
export default {
    name: 'MainComponent',
    components: {
        MovieCard
    },
    props: {
        arrayFilms: Array,
    },
}
</script>

<style lang="scss" scoped>

</style>