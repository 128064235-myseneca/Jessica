<template>
    <div >
        <b-container class="bv-example-row">
            <b-row class="text-left">
                
                <b-col cols='4' >
                     <img  class="curve" :src=image :alt= image>
                    
                </b-col>
            
                <b-col class="info">
                 
                    <h2>{{mname}}</h2>
                    <p>{{desc}}</p>
                    
                    <p>Cast: {{actor}}</p>
                    <p>Genres: {{genres}}</p>
                    <p>Director: {{director}} </p>
                    <p>Rating:  {{rating}}</p>

                   
                </b-col>
            </b-row>
        </b-container>
        
    </div>
</template>
<script>
// import card from './card.vue'
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import json from '../../movie_dataset.json'
Vue.use(VueAxios,  axios)
export default {
    
    props:{mname: String}, 
    data() {
          return{
              myJson : json,
            apiImage:"",
            image:"",
            title:this.name,
            desc:"",
            actor:"",
            genres:"",
            rating:"",
            director:""
            // image: this.apiImage.movies[0]
        }
        
    },
    created(){

        this.mname = this.$route.query.mname
        let query = 'https://yts.mx/api/v2/list_movies.json?query_term='+this.mname
        console.warn(query)
            Vue.axios.get(query)
            .then((res) => {
                this.apiImage = res.data.data
                console.warn(res)
                this.image = res.data.data.movies[0].medium_cover_image

            });
    
        for( let movie of this.myJson){
      if (this.mname === movie['title']){
          this.desc = movie['overview']
          this.actor = movie['cast']
          this.genres = movie['genres']
          this.rating = movie['vote_average']
          this.director = movie['director']

      }
        
        
    }
        
            
        }
}
</script>
<style scoped>
.info{
    color:white;
    text-align: left;
    margin-top: 20px;
    font-family: calibri;
}
.curve{
    border-radius: 6%;
    border: 3px solid  red;
    margin-top: 20px;


}
</style>