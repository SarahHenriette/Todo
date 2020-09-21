<template>
    <div style="position: relative;width: 100%;overflow: hidden;" >
            

        <slot></slot>
        <button class="carousel__nav carousel__next" @click.prevent="next"><i class="fas fa-arrow-circle-right fa-2x"></i></button>
        <button class="carousel__nav carousel__prev" @click.prevent="prev"><i class="fas fa-arrow-circle-left fa-2x"></i></button>
        <div class="carousel__pagination">
            <button v-for="n in slidesCount" v-bind:key="n" @click="goto(n-1)" :class="{active: n - 1 === index}"></button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            index: 0,
            slides: [],
            direction: 'right'
        }
    },

    mounted(){
        this.slides = this.$children
        // console.log(this.slides)
        // this.slides.forEach((slide,  i)=>{
        //     slide.index = i
        // })
    },

    watch: {
        slides (slides){
            if(this.index>= this.slidesCount){
                this.index = this.slidesCount - 1
            }
        }
    },

    computed:{
        slidesCount(){ return this.slides.length }
    },

    methods: {

        next(){
            this.index++
            this.direction = 'right'
            if(this.index >= this.slidesCount){
                this.index = 0
            }
        },

        prev (){
            this.index--
            this.direction = 'left'

            if(this.index < 0){
                this.index = this.slidesCount - 1
            }
        },

        goto(index){

            this.direction = index > this.index ? 'right' : 'left'
            this.index = index
        }
    }
    
}
</script>



<style >


.carousel__nav{
    background-color: #000;
}

.carousel__nav i{
    color: #ffffff78;
    padding: 5px;
}


.carousel{
  position: relative;
  overflow: hidden;
}

.carousel__nav{
 position: absolute;
    top: 50%;
  

}
.carousel__prev{
    position: absolute;
   left: 15px;
}

.carousel__next{
    position: absolute;
    right: 15px;
}

.carousel__pagination{
    position: absoulte;
    bottom: 10px;
    left: 0;
    right: 0;
    text-align: center;
}

.carousel__pagination button{
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: #000;
    opacity: 0.8;
    border-radius: 0px;
    margin: 0 2px;
    cursor: pointer;
}

.carousel__pagination button.active{
    background-color: rgb(133, 11, 18);
}

</style>