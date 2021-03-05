<template>
    <div>
        <h2>Top Releases  </h2><br>
  
  <card v-for = "movie in topMovies" v-bind:key = "movie" v-bind:name = movie />
  

      </div>

</template>

<style scoped>
h2{
    color: white;
    margin-top: 100px;
    text-align: center;
    margin-left: 90px;
}
</style>

<script>


import card from './card.vue'
import json from '../../movie_dataset.json'
     

export default {
  name: 'newrel',
  data(){
    return{
      
      myJson: json,
      topMovies: []
  }
  },
  components: {
    card
  },
  created(){
    let count = 0
   
    for( let movie of this.myJson){
      if (count >3){
          break
      }
        if (movie["vote_average"]>8){
          this.topMovies.push(movie["title"])
          count++
        }
        
    }
   
  }
}
</script>
