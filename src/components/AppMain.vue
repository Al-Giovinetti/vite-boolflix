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
        PopularApiUrl :"https://api.themoviedb.org/3/movie/popular?api_key=583d8ce9b90d4a8ab4d2e53f16080836",
        PopularList:[ ],
        store
    }
  },

  methods:{
    getMyFilms(serched){
      if(serched != undefined) {
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
      }else{
        axios.get(this.PopularApiUrl)
        .then((response) => {
            console.log(response.data.results);
            this.PopularList = response.data.results
        })
        .catch(function (error) {
            console.log(error);
        });
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
    <form action="reset-pg">
      <button>
        <h1 @click="ciao">boolflix</h1>
      </button>
    </form>
    <div class="header-right d-flex">
      <FilmSearchbar @searchfilm = "getMyFilms" />
      <i class="fa-solid fa-bell"></i>
      <i class="fa-solid fa-circle-user"></i>
    </div>
  </header>
        <ContainerFilmList 
          :myfilmlist = "FilmList"
          :myserielist = "SerieList"
          :popularlist = "PopularList" />
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables.scss" as *;

  header{
    background-color: $bg-header;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem 1rem;

    form button{
      background-color: $bg-header;
      border: 0;
    }

    h1{
      color: red;
      text-transform: uppercase;
      font-weight: bold;
      cursor: pointer;
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