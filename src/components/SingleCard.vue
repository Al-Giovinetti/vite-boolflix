<script>

export default{
  name:"SingleCard",

  props:{
    title : String,
    originaltitle : String,
    language : String,
    vote :Number,
  },

  data(){
    return{

    }
    
  }

}
</script>

<template>
  <div>
    <p>{{ title }}</p>
    <p>{{ originaltitle }}</p>
    <!-- Per far la bandiera basta mettre fi fi-(2 iniziali stato ) - vedi demo -->
    <span :class="`fi fi-${language}`" v-if="language != 'en'" id="bandiera"></span>
    <span>{{ language }}</span>
    <p>{{ vote }}</p>
  </div>
  <hr>
</template>

<style lang="scss" scoped>
@import "/node_modules/flag-icons/css/flag-icons.min.css";

span#bandiera{
  padding-right: 1rem;
}

</style>
