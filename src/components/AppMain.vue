<script>
import ContainerFilmList from "./ContainerFilmList.vue"
import FilmSearchbar from "./FilmSearchbar.vue"
import axios from "axios"

export default{
  name:"AppMain",

  components:{
    ContainerFilmList,
    FilmSearchbar,
  },

  data(){
    return{
        MyApiUrl : "https://api.themoviedb.org/3/search/movie?api_key=583d8ce9b90d4a8ab4d2e53f16080836&query=",
        FilmList : [ ],
    }
  },

  methods:{
    getMyFilms(serched){
      if(serched != undefined){
        axios.get(this.MyApiUrl + serched)
        .then((response) => {
            console.log(response.data.results);
            this.FilmList = response.data.results
        })
        .catch(function (error) {
            console.log(error);
        })
      }
    }
  },

  created(){
    this.getMyFilms()
  }

}
</script>

<template>
    <main>
        <p>corpo</p>
        <FilmSearchbar @searchfilm = "getMyFilms" />
        <ContainerFilmList 
          :myfilmlist = "FilmList" />
    </main>
</template>

<style lang="scss" scoped>

</style>