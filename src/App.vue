<template>
  <div>

   <carousel>
      <carousel-slide v-for="n in slides" v-bind:key="n" >
        <img :src="'https://picsum.photos/id/101' + n + '/630/300/'" alt="" width="100%">
      </carousel-slide>
      <!-- <carousel-slide>
        <img src="https://picsum.photos/id/1010/630/300" alt="" width="100%" >
      </carousel-slide> -->

    </carousel>

    <button @click="addSlide">Ajouter un slide</button>
      <todos></todos>
    
  </div>
</template>
 

<script>

import Todos from './components/Todos'
import Carousel from './components/carousel/Carousel'
import CarouselSlide from './components/carousel/CarouselSlide'

export default {
  data(){
    return {
      slides: 5
    }
  },

  methods:{
    addSlide(){
      this.slides++
    }
  },

  components:{
    Todos, 
    Carousel,
    CarouselSlide
    
    },
}

</script>

