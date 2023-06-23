<script>
import { store } from '../store';

export default{
  name:"AppHeader",

  data(){
    return{
      store
    }
  }

}
</script>

<template>
    <header>
        <h1 onclick="reload">Boolflix</h1>
    </header>
</template>

<style lang="scss" scoped>
header{
  padding: 1rem;
  background-color: rgb(37, 36, 36);
}

h1{
  color: red;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
}

</style>