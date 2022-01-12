<template>
    <main>
        <h2>Film</h2>
        <Card v-for="movie in moviesList" :key="movie.id" />
    </main>
</template>

<script>
import Card from './Card.vue';

export default {
    name: 'All',

    components: {
        Card
    },
    props: {
        moviesList: Array
    }
}
</script>