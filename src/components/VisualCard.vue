<script>
import { imgs } from '../data'
export default {
    name: 'VisualCard',
    props: {
        visual: Object
    },
    computed: {
        visualImg() {
            if (!this.visual.poster_path) return imgs.noImage;
            return imgs.baseUrl + this.visual.poster_path;
        },
        vote() {
            return Math.ceil(this.visual.vote_average / 2)
        }
    }

}
</script>

<template>
    <ul>
        <li>{{ visual.title || visual.name }}</li>
        <li>{{ visual.original_title || visual.original_name }}</li>
        <li>{{ visual.original_language }}</li>
        <li>
            <img :src="visualImg" alt="">
        </li>
        <li>
            <i v-for="star in 5" :class="star <= vote ? 'fa-solid' : 'fa-regular'" class="fa-star"></i>
        </li>
    </ul>
</template>

<style>

</style>