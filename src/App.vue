<script>
import axios from 'axios';
import { api } from './data';
import { store } from './data/store';
import SearchTerm from './components/SearchTerm.vue'
export default {
    name: 'Boolfix',
    components: { SearchTerm },
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
        updateVisualFilter(searchedVisual) {
            this.visualFilter = searchedVisual;
        },
        fetchFilm() {

            axios.get(`${api.baseUri}/search/movie`, this.axiosConfig)
                .then(res => {

                    const apiVisuals = res.data.results;
                    store[visua] = apiVisuals.map(visual => {
                        const { title, original_title, vote_average, overview, poster_path } = visualss;
                        return {
                            title,
                            original_title,
                            vote_average,
                            overview,
                            poster_path

                        }
                    })


                })
        },

    },
}
</script>

<template>

    <search-term placeholder="Cerca un titolo" @term-change="updateVisualFilter" @form-submit="fetchFilm"></search-term>
</template>

<style>

</style>