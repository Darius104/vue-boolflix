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
      voto: 0
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
        // inseirsco dentro l'array dei film la risposta dell'api
        this.arrayFilm = response.data.results

        // ciclo per tutta lal lunghezza dell'arrayFilm 
        for(let x = 0; x <= this.arrayFilm.length; x++){
          // se nell'iterazione attuale la variabile original_lagnuage è uguale ad "it"
          if(this.arrayFilm[x].original_language === "it"){
            // sostituiamo la stringa attuale con il contenuto della variabile italia
            this.arrayFilm[x].original_language = this.italia;

          }else{
            // altrimenti se nell'iterazione attuale la variabile original_lagnuage è uguale ad "en"
            if(this.arrayFilm[x].original_language === "en"){
              // sostituiamo il contenutro della stringa attuale con il contenuto della variabile inghilterra
              this.arrayFilm[x].original_language = this.inghilterra;
            }
            // per ogni iterazione del ciclo vado a sostituire il contenuto della variabile
            // vote_avarage con il risultato di questa funzione matematica.
            // prendo il voto attuale di vote_avarage e lo divido per 2 arrotondando il risultato per eccesso
            this.arrayFilm[x].vote_average = Math.ceil(this.arrayFilm[x].vote_average / 2)
          } 
        }
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
        // inserisco dentro all'array vuoto arraySerie la risposta dell'api
        this.arraySerie = response.data.results

        // ciclo per tutta lal lunghezza dell'arraySerie 
        for(let x = 0; x <= this.arraySerie.length; x++){
          // se nell'iterazione attuale la variabile original_lagnuage è uguale ad "it"
          if(this.arraySerie[x].original_language === "it"){
            // sostituiamo la stringa attuale con il contenuto della variabile italia
            this.arraySerie[x].original_language = this.italia;

          }else{
            // altrimenti se nell'iterazione attuale la variabile original_lagnuage è uguale ad "en"
            if(this.arraySerie[x].original_language === "en"){
              // sostituiamo il contenutro della stringa attuale con il contenuto della variabile inghilterra
              this.arraySerie[x].original_language = this.inghilterra;
            }
            // per ogni iterazione del ciclo vado a sostituire il contenuto della variabile
            // vote_avarage con il risultato di questa funzione matematica.
            // prendo il voto attuale di vote_avarage e lo divido per 2 arrotondando il risultato per eccesso
            this.arraySerie[x].vote_average = Math.ceil(this.arraySerie[x].vote_average / 2)
          } 
        }
      })
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
