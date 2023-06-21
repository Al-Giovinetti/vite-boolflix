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
      NationsWithoutFlag:["en","ja","ko","te","zh"]
    }
    
  }

}
</script>

<template>
  <div>
    <p>{{ title }}</p>
    <p>{{ originaltitle }}</p>
    <!-- Per far la bandiera basta mettre fi fi-(2 iniziali stato ) - vedi demo -->
    <div class="box-language">
      <span v-if="NationsWithoutFlag.includes(language)" class="fi fi-xx"> {{ language }} </span>
      <span v-else :class="`fi fi-${language}`"> {{ language }} </span>
    </div>
    <p>{{ vote }}</p>
  </div>
  <hr>
</template>

<style lang="scss" scoped>
@import "/node_modules/flag-icons/css/flag-icons.min.css";

div.box-language{
  color: white;
  background-color: black;
  padding: 0.5rem;
  .fi{
  width: 70px;
  }
}
</style>