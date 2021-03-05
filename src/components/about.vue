<template>
    <div>

        <!-- <details/> -->
        <MovieDetails/>
    <recomend  />
        
    </div>
</template>


<script>
import MovieDetails from './MovieDetails.vue'
import recomend from './recomend.vue'


export default {
  data(){
      return{
            name:""
            // image: this.apiImage.movies[0]
        }
  },
  components: {

    MovieDetails,
    recomend
    // newrel
    
  }
}
</script> 