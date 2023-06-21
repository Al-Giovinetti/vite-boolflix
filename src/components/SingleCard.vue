<script>

export default{
  name:"SingleCard",

  props:{
    title : String,
    originaltitle : String,
    language : String,
    vote :Number,
  }

}
</script>

<template>
  <p>{{ title }}</p>
  <p>{{ originaltitle }}</p>
  <p>{{ language }}</p>
  <p>{{ vote }}</p>
  <hr>
</template>

<style lang="scss" scoped>
@import "/node_modules/flag-icons/css/flag-icons.min.css";

</style>