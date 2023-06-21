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
        MyApiUrl : "https://api.themoviedb.org/3/discover/movie?api_key=583d8ce9b90d4a8ab4d2e53f16080836",
        FilmList : [ ],
    }
  },

  methods:{
    getTotalFilmList(){
        axios.get(this.MyApiUrl)
        .then((response) => {
            console.log(response.data.results);
            this.FilmList = response.data.results
        })
        .catch(function (error) {
            console.log(error);
        })
    }
  },

  created(){
    this.getTotalFilmList()
  }

}
</script>

<template>
    <main>
        <p>corpo</p>
        <FilmSearchbar />
        <ContainerFilmList />
    </main>
</template>

<style lang="scss" scoped>

</style>