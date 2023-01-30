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

    <div class="visual-container">

        <div class="visual-image">
            <img :src="visualImg" alt="">


            <div class="visual-information">
                <ul>
                    <li><b>Title:</b>{{ visual.title || visual.name }}</li>
                    <li><b>Original Title:</b>{{ visual.original_title || visual.original_name }}</li>
                    <li>
                        <b>Original Language:</b>
                        <img v-if="hasFlag" :src="flagSrc" class="flag" alt="">
                        <div v-else>{{ visual.original_language }}</div>
                    </li>

                    <li>
                        <b>Vote:</b>
                        <i v-for="star in 5" :class="star <= vote ? 'fa-solid' : 'fa-regular'" class="fa-star"></i>
                    </li>
                    <li><b>Release Date:</b>{{ visual.release_date }}</li>
                    <li><b>Overview:</b>{{ visual.overview }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.visual-container {
    width: 342px;
    border: 1px solid black;
    background-color: black;
    color: white;
    border-radius: 10px;
    margin: 10px;
    overflow-y: auto;
    position: relative;


    display: flex;
    flex-direction: column;


    ul {
        padding: 10px;

        li {
            padding-top: 5px;

            .flag {
                width: 30px;
            }


            .fa-star {
                color: rgb(228, 167, 0);
            }
        }
    }
}



.visual-information {
    display: none;
    position: absolute;
    top: 0px;
    background-color: rgba($color: #000000, $alpha: 0.8);
    width: 100%;
    height: 100%;
}

.visual-image:hover .visual-information {
    display: block;
}
</style>