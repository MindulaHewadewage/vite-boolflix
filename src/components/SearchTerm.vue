<script>
export default {
    name: 'SearchTerm',
    data: () => ({ searchedVisual: '' }),

    props: {
        placeholder: String
    },
    emits: ['form-submit', 'term-change']
}
</script>

<template>
    <form @submit.prevent="$emit('form-submit')">
        <input type="text" v-model.trim="searchedVisual" :placeholder="placeholder"
            @keyup="$emit('term-change', searchedVisual)">
        <button type="submit">cerca</button>
    </form>
</template>

<style>

</style>