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
  <div class="d-flex">
    <input type="text" name="searched-film" id="searched-film" v-model="SerchedFilm">
    <button @click="$emit('searchfilm',SerchedFilm)">
      <i class="fa-solid fa-magnifying-glass"></i>
    </button>
  </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables.scss" as *;

div{
  padding: 1rem;
  align-items: center;
}

input{
  background-color: $bg-header;
  color: white;
  border: 2px solid white;
  border-radius: 10px;
  padding: 0.2rem;
}

button{
  padding: 0.2rem;
  margin-left:0.5rem;
  background-color: $bg-header;
  border: $bg-header;
  cursor: pointer;
    i{
      color: white;
      font-size: 1.3rem;
    }
}

</style>