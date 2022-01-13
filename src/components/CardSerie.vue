<template>
    <div class="movie">
        <div>Titolo: {{infoSerie.name}}</div>
        <div>Titolo Originale: {{infoSerie.original_name}}</div>
        <div class="lingua">Lingua: </div>
        <img class="bandiera" :src="infoSerie.original_language" :alt="infoSerie.original_language">
        <div>Voto: {{ infoSerie.vote_average }}</div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        infoSerie: Object
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