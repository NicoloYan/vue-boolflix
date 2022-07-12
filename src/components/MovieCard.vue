<template>
    <div>
        <h1>{{ filmData.title }}</h1>
        <h2>{{ filmData.original_title }}</h2>
        <h3>{{ filmData.original_language }}</h3>
        <h4>{{ filmData.vote_average }}</h4>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        filmData: Object,
    },
}
</script>

<style lang="scss" scoped>

</style>