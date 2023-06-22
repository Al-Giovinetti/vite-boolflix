<script>

export default{
  name:"SingleCard",

  props:{
    title : String,
    originaltitle : String,
    language : String,
    vote :Number,
    image :String
  },

  data(){
    return{
      NationsWithoutFlag:["en","ja","ko","te","zh"],
      newVote : Math.ceil(this.vote / 2),
    } 
  },

  methods:{
    getImage(urlElement){
      return new URL(`https://image.tmdb.org/t/p/original/${urlElement}`)
    },
    getDifference(vote){
      return 5 - this.newVote
    }
  }

}
</script>

<template>
  <div class="card">
    <div class="box-img">
      <img v-if="image != null" :src="getImage(image)" :alt="title+ 'poster'">
      <img v-else src="https://cdn1.vectorstock.com/i/1000x1000/13/55/background-in-a-matrix-style-green-random-numbers-vector-39461355.jpg" alt="random background">
    </div>
    <div class="box-text">
      <p>{{ title }}</p>
      <p>{{ originaltitle }}</p>
    </div>
    <!-- Per far la bandiera basta mettre fi fi-(2 iniziali stato ) - vedi demo -->
    <div class="box-language">
      <span v-if="NationsWithoutFlag.includes(language)" class="fi fi-xx">  </span>
      <span v-else :class="`fi fi-${language}`">  </span>
    </div>
    <div class="box-star">
      <span>{{ newVote }}</span>
      <i v-for="n in newVote" class="fa-solid fa-star"></i>
      <i v-for="n in getDifference(newVote)" class="fa-regular fa-star"></i>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "/node_modules/flag-icons/css/flag-icons.min.css";

div.card{
  margin: 1rem;
  text-align: center;
  width: 180px;
}

div.box-img{
  height: 250px;
  width: 180px;
  img{
    height: 100%;
    width: 100%;
    display: block;
    object-fit: cover;
  }
}
div.box-text{
  height: 80px;
}
div.box-language{
  color: white;
  background-color: black;
  padding: 0.5rem;
  .fi{
  width: 70px;
  }
}

</style>