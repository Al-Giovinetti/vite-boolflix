<script>

export default{
  name:"FilmSearchbar",

  data(){
    return{
        SerchedFilm:"",
    }
  }

}
</script>

<template>
    <input type="text" name="searched-film" id="searched-film" v-model="SerchedFilm">
    <button @click="$emit('searchbar')">cerca</button>
    <span>{{ SerchedFilm }}</span>
</template>

<style lang="scss" scoped>

</style>