<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default{
  name:"App",

  components:{
    AppMain,
    AppHeader,
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />


</template>

<style lang="scss">
  @import "./styles/general.scss"
</style>
