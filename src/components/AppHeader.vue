<script>
import SearchTerm from './SearchTerm.vue'
export default {
    name: 'AppHeader',
    components: { SearchTerm },
    methods: {

    },
    emits: ['form-submit', 'term-change']

}


</script>

<template>
    <header>
        <div class="container">

            <section class="logo">
                <img src="../assets/img/logonetflix.png" alt="logo-neflix">
            </section>
            <section class="search">
                <search-term placeholder="Cerca un titolo" @term-change="$emit('term-change', $event)"
                    @form-submit="$emit('form-submit')"></search-term>
            </section>
        </div>
    </header>
</template>

<style scoped lang="scss">
header {
    background-color: black;
    padding: 10px;
}

.container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo img {
    width: 200px;
}
</style>