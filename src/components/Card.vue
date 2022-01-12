<template>
    <div class="movie">
        <div>Titolo: {{info.title}}</div>
        <div>Titolo Originale: {{info.original_title}}</div>
        <div>Lingua: {{info.original_language}}</div>
        <div>Voto: {{info.vote_average}}</div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
.movie{
    margin: 20px;
    border: 1px solid black;
}
</style>