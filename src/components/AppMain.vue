<script>
import ContainerFilmList from "./ContainerFilmList.vue"
import FilmSearchbar from "./FilmSearchbar.vue"
import axios from "axios"
import { store } from "../store"

export default{
  name:"AppMain",

  components:{
    ContainerFilmList,
    FilmSearchbar,
  },

  data(){
    return{
        FilmApiUrl : "https://api.themoviedb.org/3/search/movie?api_key=583d8ce9b90d4a8ab4d2e53f16080836&query=",
        FilmList : [ ],
        SerieApiUrl : "https://api.themoviedb.org/3/search/tv?api_key=583d8ce9b90d4a8ab4d2e53f16080836&query=",
        SerieList : [ ],
        store
    }
  },

  methods:{
    getMyFilms(serched){
      if(serched != undefined){
        axios.get(this.FilmApiUrl + serched)
        .then((response) => {
            console.log(response.data.results);
            this.FilmList = response.data.results
        })
        .catch(function (error) {
            console.log(error);
        });
        axios.get(this.SerieApiUrl + serched)
        .then((response) => {
            console.log(response.data.results);
            this.SerieList = response.data.results
        })
        .catch(function (error) {
            console.log(error);
        });
        this.store.searchIsDone = true
      }
    },

  },

  created(){
    this.getMyFilms()
  },

}
</script>

<template>
    <main>
        <FilmSearchbar @searchfilm = "getMyFilms" />
        <ContainerFilmList 
          :myfilmlist = "FilmList"
          :myserielist = "SerieList" />
    </main>
</template>

<style lang="scss" scoped>

</style>