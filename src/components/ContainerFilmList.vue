<script>
import SingleCard from "./SingleCard.vue"

export default{
  name:"ContainerFilmList",

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
        <SingleCard v-for="film in myfilmlist"
        :title = film.title
        :originaltitle = film.original_title
        :language = film.original_language
        :vote = film.vote_average
        :image = film.poster_path
          />
        <SingleCard v-for="serie in myserielist" 
        :title = serie.name
        :originaltitle = serie.original_name
        :language = serie.original_language
        :vote = serie.vote_average 
        :image = serie.poster_path />
    </div>
    
</template>

<style lang="scss" scoped>

</style>