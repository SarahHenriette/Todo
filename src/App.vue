<template>
  <div>


  <div id="todoList" style="width: 70%; margin:auto" v-if="todolist">
    <todos></todos>
  </div>
  


  <div id="carousel" v-if="carousel">
<h1>Carousel</h1>
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

      
    <div id="btn">
      <button @click="afficheTodoList">TP: Todo-list</button>
    <button @click="afficheCarousel">TP: Carousel</button>
    </div>

  </div>
</template>
 

<script>

import Todos from './components/Todos'
import Carousel from './components/carousel/Carousel'
import CarouselSlide from './components/carousel/CarouselSlide'

export default {
  data(){
    return {
      slides: 5,
      carousel : false,
      todolist : true,
    }
  },

  methods:{
    addSlide(){
      this.slides++
      console.log(this.slides)
    },

  removeSlide(){
    this.slides--
  },
  
  afficheTodoList(){
    this.carousel = false
      this.todolist = true
  },


   afficheCarousel(){
      this.carousel = true
      this.todolist = false
  },

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
   display: flex;
   flex-direction: column;
  justify-content: center;
  align-items: center;
    width: 70%; 
  margin:auto;
      position: absolute;
    margin: auto;
    left: 0;
    right: 0;
    top: 150px;
}

#carousel h1{
  position: absolute;
    top: -155px;
    width: 100%;
    font-size: 100px;
    font-weight: 100;
    text-align: center;
    color: rgba(175, 47, 47, 0.15);
    -webkit-text-rendering: optimizeLegibility;
    -moz-text-rendering: optimizeLegibility;
    text-rendering: optimizeLegibility;
}

#todoList, #carousel{
  background-color: red;
  height: 600px;
 

 
}

#btn{
  display: flex;
  flex-direction: column;
  width: 200px;
  position: absolute;
  top: 150px;
}

#btn button {
  background-color: #272525;
  color: #fff;
  padding: 7px 15px;
  cursor: pointer;
}

</style>