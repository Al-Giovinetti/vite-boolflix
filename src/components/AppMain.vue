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
  <header class="d-flex">
    <h1>boolflix</h1>
    <div class="header-right d-flex">
      <FilmSearchbar @searchfilm = "getMyFilms" />
      <i class="fa-solid fa-bell"></i>
      <i class="fa-solid fa-circle-user"></i>
    </div>
  </header>
        <ContainerFilmList 
          :myfilmlist = "FilmList"
          :myserielist = "SerieList" />
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables.scss" as *;

  header{
    background-color: $bg-header;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem 1rem;

    h1{
      color: red;
      text-transform: uppercase;
      font-weight: bold;
    }

    .header-right{
      align-items: center;

      i{
        padding: 1rem;
        font-size: 1.3rem;
      }
    }
  }

</style>