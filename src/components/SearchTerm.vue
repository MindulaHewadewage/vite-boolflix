<script>
export default {
    name: 'SearchTerm',
    data() {
        return {
            term: ''
        }
    },

    props: {
        placeholder: String
    },
    emits: ['form-submit', 'term-change']
}
</script>

<template>
    <form @submit.prevent="$emit('form-submit')">
        <input type="text" v-model.trim="term" :placeholder="placeholder" @keyup="$emit('term-change', term)"
            class="searchbar">
        <button type="submit">cerca</button>
    </form>
</template>

<style scoped lang="scss">
.searchbar,
button {
    padding: 5px;
}
</style>