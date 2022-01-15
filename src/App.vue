<template>
  <div id="app">
    <!-- in ascolto del figlio Header -->
    <Header @passSearch="search" />
    <All :moviesList="arrayFilm" :serieList="arraySerie"/>
  </div>
</template>

<script>
// vari import
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
      // data
      nomeFilm: '',
      apiKey: '43b8d279f0f566005cd0114236cddf4e',
      arrayFilm: [],
      arraySerie: [],
      italia: require('./assets/italia.png'),
      inghilterra: require('./assets/Inghilterra.png'),
      voto: 0,
      none: require('./assets/noimg.png')
    }
  },
  methods: {
    // richiamo della funzione in ascolto dell'app vue e delle funzioni
    // film() & serie()
    search: function(parametro){
      this.nomeFilm = parametro
      this.film();
      this.serie();
    },
    film: function(){
      // richiediamo i film dall'api
      axios.get(
        'https://api.themoviedb.org/3/search/movie',
        {
          // parametri obbligatori
          params: {
            api_key: this.apiKey,
            query: this.nomeFilm
          }
        }
      // risposta dell'api
      ).then((response) => {
        this.arrayFilm = this.populateCard(response.data.results)
      });
    },

    serie: function(){
      // richiamiamo le seirie dall'api
      axios.get(
        'https://api.themoviedb.org/3/search/tv',
        {
          // parametri obbligatori
          params:{
            api_key: this.apiKey,
            query: this.nomeFilm
          }
        }
      // risposta dell'api
      ).then((response) =>{
        this.arraySerie = this.populateCard(response.data.results)
      })
    },

    populateCard: function(array){
        // ciclo per tutta lal lunghezza dell'array 
        for(let x = 0; x < array.length; x++){
          // se nell'iterazione attuale la variabile original_lagnuage è uguale ad "it"
          if(array[x].original_language === "it"){
            // sostituiamo la stringa attuale con il contenuto della variabile italia
            array[x].original_language = this.italia;

          }else{
            // altrimenti se nell'iterazione attuale la variabile original_lagnuage è uguale ad "en"
            if(array[x].original_language === "en"){
              // sostituiamo il contenutro della stringa attuale con il contenuto della variabile inghilterra
              array[x].original_language = this.inghilterra;
            }
            // per ogni iterazione del ciclo vado a sostituire il contenuto della variabile
            // vote_avarage con il risultato di questa funzione matematica.
            // prendo il voto attuale di vote_avarage e lo divido per 2 arrotondando il risultato per eccesso
            array[x].vote_average = Math.ceil(array[x].vote_average / 2)
          }
          // vado a controllare se l'immagine dell'array è nulla o meno
          if(array[x].backdrop_path === null){
            // inserisco l'immagine di default none
            array[x].backdrop_path = this.none
          }else{
            // altrimenti inserisco il path base + quello dell'immgaine corrente
            array[x].backdrop_path = 'http://image.tmdb.org/t/p/w500/' + array[x].backdrop_path
          }
        }
        return array;
    }
  }
};
</script>

<style lang="scss">
// reset
img{
  width: 100%;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
