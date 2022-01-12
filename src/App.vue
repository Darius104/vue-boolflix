<template>
  <div id="app">
    <Header @passSearch="search" />
    <All :moviesList="arrayFilm" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import All from './components/All.vue'
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    All
  },
  data: function(){
    return{
      nomeFilm: '',
      apiKey: '43b8d279f0f566005cd0114236cddf4e',
      arrayFilm: [],
      italia: require('./assets/italia.png'),
      inghilterra: require('./assets/Inghilterra.png'),
      voto: 0
    }
  },
  methods: {
    search: function(parametro){
      this.nomeFilm = parametro
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
        this.arrayFilm = response.data.results
        for(let x = 0; x <= 19; x++){
          if(this.arrayFilm[x].original_language === "it"){
            this.arrayFilm[x].original_language = this.italia;

          }else{
            if(this.arrayFilm[x].original_language === "en"){
              this.arrayFilm[x].original_language = this.inghilterra;

            }
            // this.arrayFilm[x].vote_average = this.voto;
            // parseInt(this.voto);
              this.arrayFilm[x].vote_average = (this.arrayFilm[x].vote_average).toFixed()
              

          } 
        }
      });
    }
  }
};
</script>

<style lang="scss">
img{
  width: 100%;
}
</style>
