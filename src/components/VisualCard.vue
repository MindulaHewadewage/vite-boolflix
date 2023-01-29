<script>
export default {
    name: 'VisualCard',
    props: {
        visual: Object
    }
}
</script>

<template>
    <ul>
        <li>{{ visual.title || visual.name }}</li>
        <li>{{ visual.original_title || visual.original_name }}</li>
        <li>{{ visual.original_language }}</li>
        <li>{{ visual.vote_average }}</li>
    </ul>
</template>

<style>

</style>