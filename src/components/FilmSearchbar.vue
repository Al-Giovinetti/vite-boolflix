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
  <div>
    <input type="text" name="searched-film" id="searched-film" v-model="SerchedFilm">
    <button @click="$emit('searchfilm',SerchedFilm)">cerca</button>
  </div>
</template>

<style lang="scss" scoped>

</style>