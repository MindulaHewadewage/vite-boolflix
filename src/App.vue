<script>
import axios from 'axios';
import { api } from './data';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue';
import SearchTerm from './components/SearchTerm.vue'
import VisualCard from './components/VisualCard.vue'
export default {
    name: 'Boolfix',
    components: { AppHeader, SearchTerm, VisualCard },
    data: () => ({ store, visualFilter: '' }),



    computed: {
        axiosConfig() {
            const { key } = api;
            return {
                params: {
                    api_key: key,
                    query: this.visualFilter
                }
            }
        }
    },

    methods: {
        updateVisualFilter(term) {
            console.log('term:', term);
            this.visualFilter = term;
            console.log(0);
        },
        searchVisual() {
            console.log(1230);
            if (!this.visualFilter) {
                store.movies = [];
                store.series = [];
                return;
            }
            this.api('search/movie', 'movies');
            this.api('search/tv', 'series');
        },
        api(endpoint, visual) {
            axios.get(`${api.baseUri}/${endpoint}`, this.axiosConfig)
                .then(res => {
                    store[visual] = res.data.results
                })
        }



    },
}
</script>


<template>
    <div class="container">
        <app-header @term-change="updateVisualFilter" @form-submit="searchVisual"></app-header>

        <main>
            <div class="movies">
                <h3>Movies</h3>
                <visual-card v-for="movie in store.movies" :key="movie.id" :visual="movie"></visual-card>
            </div>

            <div class="series">
                <h3>Series</h3>
                <visual-card v-for="serie in store.series" :key="serie.id" :visual="serie"></visual-card>

            </div>
        </main>
    </div>
</template>

<style lang="scss">
@use './assets/sass/style.scss';
</style>