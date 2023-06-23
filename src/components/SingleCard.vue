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
      NationsWithoutFlag:["en","ja","ko","te","zh","su"],
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
    <div class="back-card">
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
  </div>
</template>

<style lang="scss" scoped>
@import "/node_modules/flag-icons/css/flag-icons.min.css";
div.card{
  margin: 1rem;
  text-align: center;
  width: 300px;
  height: 500px;
  position: relative;
    &:hover div.box-img{
      opacity: 20%;
    }
    &:hover div.back-card{
      display: block;
    }
}

div.back-card{
  display: none;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
}

div.box-img{
  height: 500px;
  width: 300px;
  
  img{
    height: 100%;
    width: 100%;
    display: block;
    object-fit: cover;
  }
}
div.box-text{
  p{
    padding: 0.7rem 0;
  }
}
div.box-language{
  color: white;
  padding: 0.5rem;
  .fi{
  width: 70px;
  padding: 0.5rem;
  margin: 0.4rem;

  }
}

</style>