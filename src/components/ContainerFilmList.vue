<script>
import SingleCard from "./SingleCard.vue"
import { store } from "../store";

export default{
  name:"ContainerFilmList",

  data(){
    return{
      store
    }
  },

  components:{
    SingleCard,
  },

  props:{
    myfilmlist :Array,
    myserielist : Array
  }

}
</script>

<template>
  <div>
    <h2 v-if="store.searchIsDone == true">Film Trovati</h2>
    <div class="d-flex">
      <SingleCard v-for="film in myfilmlist" 
        :title = film.title
        :originaltitle = film.original_title
        :language = film.original_language
        :vote = film.vote_average
        :image = film.poster_path
      />
    </div>
    <h2 v-if="store.searchIsDone == true">Serie trovate</h2>
    <div class="d-flex">
        <SingleCard v-for="serie in myserielist" 
        :title = serie.name
        :originaltitle = serie.original_name
        :language = serie.original_language
        :vote = serie.vote_average 
        :image = serie.poster_path />
    </div>
  </div>
    
</template>

<style lang="scss" scoped>
h2{
  padding: 1rem;
}
div.d-flex{
  overflow-x:auto;
}
::-webkit-scrollbar{
  width: 0;
}


</style>