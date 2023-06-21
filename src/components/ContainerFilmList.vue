<script>
import SingleCard from "./SingleCard.vue"

export default{
  name:"ContainerFilmList",

  components:{
    SingleCard,
  },

  props:{
    myfilmlist :Array,
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
          />
    </div>
    
</template>

<style lang="scss" scoped>

</style>