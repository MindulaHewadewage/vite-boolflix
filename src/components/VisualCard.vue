<script>
export default {
    name: VisualCard,
    props: {
        preset: Object
    }
}
</script>

<template>
    <ul>
        <li>{{ preset.title || preset.name }}</li>
        <li>{{ preset.original_title || preset.original_name }}</li>
        <li>{{ preset.original_language }}</li>
        <li>{{ preset.vote_average }}</li>
    </ul>
</template>

<style>

</style>