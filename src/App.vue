<template>
  <div>

   <carousel>
      <carousel-slide>
        <img src="https://picsum.photos/id/1010/630/300/" alt="" width="100%">
      </carousel-slide>
      <carousel-slide>
        <img src="https://picsum.photos/id/1010/630/300" alt="" width="100%">
      </carousel-slide>

    </carousel>

      <todos></todos>
    
  </div>
</template>
 

<script>

import Todos from './components/Todos'
import Carousel from './components/carousel/Carousel'
import CarouselSlide from './components/carousel/CarouselSlide'



export default {

  components:{
    Todos, 
    Carousel,
    CarouselSlide
    
    },
}
</script>

