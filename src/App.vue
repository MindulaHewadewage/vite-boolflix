<script>
import axios from 'axios';
import { api } from './data';
import { store } from './data/store';
import SearchTerm from './components/SearchTerm.vue'
import VisualCard from './components/VisualCard.vue'
export default {
    name: 'Boolfix',
    components: { SearchTerm, VisualCard },
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
            this.visualFilter = term;
        },
        searchVisual() {
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
    <header>
        <search-term placeholder="Cerca un titolo" @term-change="updateVisualFilter"
            @form-submit="searchVisual"></search-term>
    </header>

    <main>
        <visual-card v-for=""></visual-card>
    </main>

</template>

<style>

</style>