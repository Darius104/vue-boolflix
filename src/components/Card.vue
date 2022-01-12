<template>
    <div class="movie">
        <div>Titolo: {{info.title}}</div>
        <div>Titolo Originale: {{info.original_title}}</div>
        <div class="lingua">Lingua: </div>
        <img class="bandiera" :src="info.original_language" :alt="info.original_language">
        <div>Voto: {{ info.vote_average }}</div>
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
    .lingua{
        display: inline-block;
    }
    .bandiera{
        width: 20px;
    }
}
</style>