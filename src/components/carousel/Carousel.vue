<template>
    <div>
        <slot></slot>
        <button class="carousel__nav carousel__next" @click.prevent="next"><i class="fas fa-arrow-circle-right fa-3x"></i></button>
        <button class="carousel__nav carousel__prev" @click.prevent="prev"><i class="fas fa-arrow-circle-left fa-3x"></i></button>

    </div>
</template>

<script>
export default {
    data(){
        return{
            index: 0,
            slides: []
        }
    },

    mounted(){
        this.slides = this.$children
        this.slides.forEach((slide,  i)=>{
            slide.index = i
        })
    },

    computed:{
        slidesCount(){ return this.slides.length }
    },

    methods: {

        next(){
            this.index++
            if(this.index >= this.slidesCount){
                this.index = 0
            }
        },

        prev (){
            this.index--
            if(this.index < 0){
                this.index = this.slidesCount - 1
            }
        }
    }
    
}
</script>



<style >

.carousel{
  position: relative;
}

.carousel__nav{
  position: absolute;
 top:150px;


}
.carousel__prev{
    position: absolute;
   left: 25px;
}

.carousel__next{
    position: absolute;
    right: 25px;
}

</style>