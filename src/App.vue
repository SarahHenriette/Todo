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

    <div id="btn-carousel">
          <button @click="addSlide"><i class="fas fa-plus-circle fa-2x"></i></button>
        <button @click="removeSlide"><i class="fas fa-trash-alt fa-2x"></i></button>
    </div>
  </div>

   <div id="form" v-if="formulaire">
    <test-form></test-form>
  </div>
      
    <div id="btn">
      <button @click="afficheTodoList">TP: Todo-list</button>
    <button @click="afficheCarousel">TP: Carousel</button>
    <button @click="afficheFormulaire">Test : Formulaire</button>

    </div>


 
  </div>


  
</template>
 

<script>

import Todos from './components/Todos'
import TestForm from './components/Form'

import Carousel from './components/carousel/Carousel'
import CarouselSlide from './components/carousel/CarouselSlide'

export default {
  data(){
    return {
      slides: 5,
      carousel : false,
      todolist : true,
      formulaire : false,
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
    this.formulaire = false

      this.todolist = true
  },


   afficheCarousel(){
      this.carousel = true
    this.formulaire = false

      this.todolist = false
  },
     afficheFormulaire(){
    this.formulaire = true

      this.carousel = false
      this.todolist = false
  },

  },

  components:{
    Todos, 
    Carousel,
    CarouselSlide, 
    TestForm
    
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

#btn-carousel {
  display: flex;
  position: absolute;
  bottom: 0;
  right: 0;
}

#btn-carousel button{
  padding: 10px 20px; 
  margin-left: 10px;
  background-color: #d6d6d6;
  
}

#todoList, #carousel{
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
  background-color: #ab3232;
  color: #fff;
  padding: 15px 15px;
  cursor: pointer;
  margin-top: 5px;

}

#form{
  margin: auto;
  width: 50%;
}

</style>