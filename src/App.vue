<script>
import axios from 'axios';
import { store } from './data/store';
export default {
    data() {
        return {
            store
        }
    },

    methods: {
        fetchFilm() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=705540f12290ed130ac0a76c5259312d&query=anelli')
                .then(res => {
                    store.visuals = res.data

                })
        }

    },
    created() {
        this.fetchFilm()
    }
}
</script>

<template>
    <header>

    </header>
</template>

<style>

</style>