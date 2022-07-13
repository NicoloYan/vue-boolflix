<template>
    <div>
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
    </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
    name: 'MovieCard',
    components: {
        LangFlag,
    },
    props: {
        filmData: Object,
    },
}
</script>

<style lang="scss" scoped>

</style>