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
    <button @click="$emit('searchfilm',SerchedFilm)">
      <i class="fa-solid fa-magnifying-glass"></i>
    </button>
  </div>
</template>

<style lang="scss" scoped>

</style>