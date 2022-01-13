<template>
    <div class="containerCard">
        <div class="movie">
            <div class="information">
                <div>Titolo: {{info.title}}</div>
                <div>Titolo Originale: {{info.original_title}}</div>
                <div>Lingua: </div>
                <img class="bandiera" :src="info.original_language" :alt="info.original_language">
                <div>
                    Voto:
                    <i class="fas fa-star" v-for="(elemento, indice) in info.vote_average" :key="indice" ></i>
                    <i class="far fa-star" v-for="(element, ind) in (5 - info.vote_average)" :key="ind"></i>
                </div>
            </div>
            <div><img class="foto" :src="'http://image.tmdb.org/t/p/w500/' + info.backdrop_path" alt=""></div>
            
        </div>
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
.containerCard{
    flex-basis: 25%;
    position: relative;
    .movie{
        margin: 20px;

        .information{
            position: absolute;
            top: -80%;
            z-index: 0;
        }
        .lingua{
            display: inline-block;
        }
        .bandiera{
            width: 20px;
        }
        .foto{
            width: 100%;
            z-index: 2;
            &:hover{
                display: none;
            }
        }
    }
}
</style>