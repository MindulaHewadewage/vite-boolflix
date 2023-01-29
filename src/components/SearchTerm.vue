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
    <form @submit.prevent="$emit('form-submit')">
        <input type="text" v-model.trim="searchedVisual" :placeholder="placeholder" @keyup="$emit('term-change', term)">
        <button type="submit">cerca</button>
    </form>
</template>

<style>

</style>