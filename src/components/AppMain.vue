<script>
import AppHeader from "./AppHeader.vue"
import ContainerFilmList from "./ContainerFilmList.vue"
import FilmSearchbar from "./FilmSearchbar.vue"
import axios from "axios"
import { store } from "../store"

export default{
  name:"AppMain",

  components:{
    AppHeader,
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
  <header class="d-flex">
    <AppHeader />
    <FilmSearchbar @searchfilm = "getMyFilms" />
    <div class="icon d-flex">

    </div>
  </header>
        <ContainerFilmList 
          :myfilmlist = "FilmList"
          :myserielist = "SerieList" />
</template>

<style lang="scss" scoped>

</style>