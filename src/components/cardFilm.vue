<script >
    export default {
    name: 'cardFilm',
    props:{
       filmElement: Object
    },
    data(){
      return {
         flags:['en.jpg','fr.jpg','it.png',],
      }
    },
    methods:{
      isFlagPresent(language){
         if(this.flags.includes(language+'.jpg')){
          return true
         }
         return false;
     },

     getImagePath(imgSource){
      return new URL(`../assets/img/${imgSource}.jpg`, import.meta.url);
     }
    }
    
}
   </script>
   
   <template>
         <div class="col-3 p-2 myCard "> 
            <p>Titolo:{{ filmElement.title }}</p>
            <p>Titolo originale:{{ filmElement.original_title }}</p>
            <div>
               <span v-if="isFlagPresent(filmElement.original_language)">
                  <span>Lingua originale:</span><img  
                  :src="getImagePath(filmElement.original_language)" alt="img">
               </span>
              
               <span v-else>
                  <p>Lingua originale:{{ filmElement.original_language}}</p>
               </span>
            </div>
            <p>Voto:{{ filmElement.vote_average }}</p>
         </div>
   </template>
   
   <style scoped>
    .myCard{
    border:1px solid black;
    
  }
  img{
   width: 5vw;
  }

   </style>