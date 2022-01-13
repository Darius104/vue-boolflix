<template>
    <div class="containerCard">
        <div class="movie">
            <div><img class="foto" :src="'http://image.tmdb.org/t/p/w500/' + infoSerie.backdrop_path" alt=""></div>
            <div>Titolo: {{infoSerie.name}}</div>
            <div>Titolo Originale: {{infoSerie.original_name}}</div>
            <div class="lingua">Lingua: </div>
            <img class="bandiera" :src="infoSerie.original_language" :alt="infoSerie.original_language">
            <div>
                Voto:
                <i class="fas fa-star" v-for="(elemento, indice) in infoSerie.vote_average" :key="indice" ></i>
                <i class="far fa-star" v-for="(element, ind) in (5 - infoSerie.vote_average)" :key="ind"></i>
            </div>
        </div>
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
.containerCard{
    flex-basis: 20%;
    
    .movie{
        margin: 20px;
        border: 1px solid black;
        height: 400px;
        .lingua{
            display: inline-block;
        }
        .bandiera{
            width: 20px;
        }
        .foto{
            width: 250px;
        }
    }
}
</style>