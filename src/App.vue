<script>
import axios from 'axios';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue';
import SearchTerm from './components/SearchTerm.vue'
export default {
    data() {
        return {
            store,
            writtenName: ''
        }
    },

    components: { AppHeader, SearchTerm },

    methods: {
        fetchFilm() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=705540f12290ed130ac0a76c5259312d&query=anelli')
                .then(res => {

                    const apiVisuals = res.data.results;
                    store.visuals = apiVisuals.map(visual => {
                        const { title, original_title, vote_average, overview, poster_path } = visual;
                        return {
                            title,
                            original_title,
                            vote_average,
                            overview,
                            poster_path

                        }
                    })


                })
        }

    },
    created() {
        this.fetchFilm()
    }
}
</script>

<template>
    <app-header></app-header>
    <search-term></search-term>
</template>

<style>

</style>