<template>
    <div class="header">
        <div class="boolflix">
            <h1>BOOLFLIX</h1>
        </div>
        <div class="searchbar">
            <input
                @keyup.enter="ricercaFilm()"
                type="text"
                name="film"
                id="film"
                placeholder="Type here to search"
                v-model="FilmCercato"
            />
            <button @click="ricercaFilm()">Search</button>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'HeaderComponent',
    data() {
        return {
            FilmCercato: "",
            arrayFilms: null,
            arraySeries: null,
        };
    },
    methods: {
        ricercaFilm() {
        if (this.FilmCercato.trim() == "") {
            this.arrayFilms = null;
            this.$emit("ricercaFilm", this.arrayFilms);
        } else {
            axios
            .get(
                `https://api.themoviedb.org/3/search/movie?api_key=17b895e4aecb3dd738db6f696031adb0&query=${this.FilmCercato}`
            )
            .then((response) => {
                this.arrayFilms = response.data.results;
                this.$emit("ricercaFilm", this.arrayFilms);
            })
                .then(() => {
                    axios
                    .get(
                        `https://api.themoviedb.org/3/search/tv?api_key=17b895e4aecb3dd738db6f696031adb0&language=it_IT&query=${this.FilmCercato}`
                    )
                    .then((responseTV) => {
                        this.arraySeries = responseTV.data.results;
                        this.$emit("ricercaSerie", this.arraySeries);
                        this.FilmCercato = ''
                    });
                });
            }
        },
    },
}
</script>

<style lang="scss" scoped>
.header {
    height: 70px;
    display: flex;
    justify-content: space-between;
    background-color: black;
}
h1 {
    color: red;
    font-size: 30px;
    line-height: 70px;
    margin-left: 20px;
}
.searchbar {
    line-height: 70px;
    margin-right: 20px;
}
</style>