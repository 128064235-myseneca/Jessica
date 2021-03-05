<template>
    <div class="recomendtext">
        <h1>RECOMMENDED MOVIES FOR YOU</h1>
        <h5 >(click any of the movies to get recommendation)</h5>
  <!-- <card :name = movie1 />
  <card :name= this.movie2 />
  <card :name= this.movie3 /> -->
  <!-- <card name="Avatar"/>
   <card name="Avatar"/>
    <card name="Avatar"/>
     <card name="Avatar"/> -->
  <!-- <card :name = this.movie4 /> -->
  <card v-for = "movie in movies" v-bind:key = "movie" v-bind:name = movie />
  

  </div>

</template>

<script>

import card from './card.vue'
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios,  axios)
export default {
  name: 'recomend',
  props:{mname: String}, 
  data() {
          return{
            apiname:"",
            image:"",
            
            movies:"",
            

            // image: this.apiImage.movies[0]
        }
        
    },
  components: {
  card
  },
 created(){
    console.warn(this.$route.query)
    this.mname = this.$route.query.mname
    let query = 'http://127.0.0.1:5000/getmovie?movie='+this.mname
    console.warn(query)
    Vue.axios.get(query)
      .then((res) => {
       this.movies = [res.data[1],res.data[2],res.data[3],res.data[4]]
      
        
            });
        }
}
</script>

<style scoped>
.recomendtext{
    margin-top: 60px;
    color:white;
    font-family: Cambria;
}
</style>