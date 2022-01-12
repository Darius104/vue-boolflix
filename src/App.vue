<template>
  <div id="app">
    <Header @passSearch="search" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
  },
  data: function(){
    return{
      nomeFilm: '',
      apiKey: '43b8d279f0f566005cd0114236cddf4e'
    }
  },
  methods: {
    search: function(p){
      this.nomeFilm = p
      this.film();
    },
    film: function(){
      axios.get(
        'https://api.themoviedb.org/3/search/movie',
        {
          params: {
            api_key: this.apiKey,
            query: this.nomeFilm
          }
        }
      ).then((response) => {
        console.log(response)
      });
    }
  }
};
</script>

<style lang="scss">

</style>
