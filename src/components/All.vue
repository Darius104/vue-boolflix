<template>
    <main>
        <h2>Film</h2>
        <div class="contenitore">
            <!-- stampiamo nel dom le varie card Film tramite un v-for -->
            <Card v-for="movie in moviesList" :key="movie.id" :info="movie"/>
        </div>

        <h2>Serie</h2>
        <div class="contenitore">
            <!-- stampiamo nel dom le varie card Serie tramite un v-for -->
            <CardSerie v-for="serie in serieList" :key="serie.id" :infoSerie="serie"/>
        </div>
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
    // importo gli array con le props
    props: {
        moviesList: Array,
        serieList: Array
    }
}
</script>

<style lang="scss" scoped>
main{
    height: calc(100vh - 100px);
    background-color: gray;
    overflow-y: hidden;
    overflow-y: auto;

    .contenitore{
        display: flex;
        justify-content: space-between;
        flex-direction: row;
        flex-wrap: wrap;
    }
}
</style>