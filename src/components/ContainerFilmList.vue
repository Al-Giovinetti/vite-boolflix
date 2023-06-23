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
    myserielist : Array,
    popularlist : Array
  }

}
</script>

<template>
  <div id="popular-box">
    <h2 v-if="store.searchIsDone == false">I più popolari</h2>
    <div v-if="store.searchIsDone == false" class="popular d-flex" >
      <SingleCard v-for="film in popularlist" 
        :title = film.title
        :originaltitle = film.original_title
        :language = film.original_language
        :vote = film.vote_average
        :image = film.poster_path
      />
    </div>
    <div  v-if="store.searchIsDone == true" id="searched-box">
      <h2 >Film Trovati</h2>
      <div class="d-flex">
        <SingleCard v-for="film in myfilmlist" 
          :title = film.title
          :originaltitle = film.original_title
          :language = film.original_language
          :vote = film.vote_average
          :image = film.poster_path
        />
      </div>
      <h2 >Serie trovate</h2>
      <div class="d-flex">
          <SingleCard v-for="serie in myserielist" 
          :title = serie.name
          :originaltitle = serie.original_name
          :language = serie.original_language
          :vote = serie.vote_average 
          :image = serie.poster_path />
      </div>
    </div>
  </div>
    
</template>

<style lang="scss" scoped>
h2{
  padding: 1rem;
}

.popular{
  flex-wrap: wrap;
  justify-content: center;

}
#searched-box .d-flex{
  overflow-x:auto;
}
::-webkit-scrollbar{
  width: 0;
}


</style>