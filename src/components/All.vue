<template>
    <main>
        <h2>Film</h2>
        <Card v-for="movie in moviesList" :key="movie.id" :info="movie"/>

        <h2>Serie</h2>
        <CardSerie v-for="serie in serieList" :key="serie.id" :infoSerie="serie"/>
    </main>
</template>

<script>
import Card from './Card.vue';
import CardSerie from './CardSerie.vue'

export default {
    name: 'All',

    components: {
        Card,
        CardSerie
    },
    props: {
        moviesList: Array,
        serieList: Array
    }
}
</script>