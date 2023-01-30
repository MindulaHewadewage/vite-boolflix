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
        },
        hasFlag() {
            const flags = ['it', 'en', 'es', 'fr', 'de', 'pt', 'tr'];
            return flags.includes(this.visual.original_language);
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.visual.original_language}.png`, import.meta.url);
            return url.href;
        }
    }

}
</script>

<template>

    <ul class="visual-container">
        <li>{{ visual.title || visual.name }}</li>
        <li>{{ visual.original_title || visual.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" class="flag" alt="">
            <div v-else>{{ visual.original_language }}</div>
        </li>
        <li>
            <!-- <img :src="visualImg" alt=""> -->
        </li>
        <li>
            <i v-for="star in 5" :class="star <= vote ? 'fa-solid' : 'fa-regular'" class="fa-star"></i>
        </li>
        <li>{{ visual.overview }}</li>
    </ul>
</template>

<style scoped lang="scss">
.visual-container {
    width: 342px;
    height: 513px;
    border: 1px solid black;
    border-radius: 10px;
    padding: 10px;
    overflow-y: auto;



    display: flex;
    flex-direction: column;

}

.flag {
    width: 30px;
}
</style>