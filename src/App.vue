<template>
  <div>


  <div id="todoList" style="width: 70%; margin:auto">
    <todos></todos>
  </div>
  


  <div id="carousel">
     <carousel>
      <carousel-slide v-for="n in slides" v-bind:key="n" :index="n - 1">
        <img :src="'https://picsum.photos/id/101' + n + '/630/300/'" alt="" width="100%">
      </carousel-slide>
      <!-- <carousel-slide>
        <img src="https://picsum.photos/id/1010/630/300" alt="" width="100%" >
      </carousel-slide> -->

    </carousel>

    <button @click="addSlide">Ajouter un slide</button>
    <button @click="removeSlide">Supprimer un slide</button>
  </div>

      
    <button>TP: Todo-list</button>
    <button>TP: Carousel</button>

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
      console.log(this.slides)
    },

  removeSlide(){
    this.slides--
  }

  },

  components:{
    Todos, 
    Carousel,
    CarouselSlide
    
    },
}

</script>

<style>

#carousel{
    display: block;
  position: relative;
    width: 70%; 
  margin:auto;
}

</style>