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
        }
    }

}
</script>

<template>
    <ul>
        <li>{{ visual.title || visual.name }}</li>
        <li>``</li>
        <li>{{ visual.original_title || visual.original_name }}</li>
        <li>{{ visual.original_language }}</li>
        <li>
            <img :src="visualImg" alt="">
        </li>
        <li>{{ visual.vote_average }}</li>
    </ul>
</template>

<style>

</style>