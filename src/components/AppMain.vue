<script>
import ContainerFilmList from "./ContainerFilmList.vue"
import FilmSearchbar from "./FilmSearchbar.vue"
export default{
  name:"AppMain",

  components:{
    ContainerFilmList,
    FilmSearchbar,
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