<script>
export default {
    name: 'SearchTerm',
    data() {
        return {
            searchedVisual: '',
            placeholder: ''
        }
    },
    props: {
        placeholder: String
    },
    emits: ['term-change']
}
</script>

<template>
    <form>
        <input type="text" v-model.trim="searchedVisual" :placeholder="placeholder" @keyup="$emit('term-change', term)">
        <button>cerca</button>
    </form>
</template>

<style>

</style>