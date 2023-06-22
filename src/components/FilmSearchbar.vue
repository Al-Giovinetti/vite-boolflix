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
div{
  padding: 1rem;
}

input{
  background-color: black;
  color: white;
  border: 2px solid white;
  border-radius: 10px;
  padding: 0.2rem;
}

button{
  padding: 0.2rem;
  margin-left:0.5rem;
  background-color: black;
  border: black;
  cursor: pointer;
    i{
      color: white;
    }
}

</style>