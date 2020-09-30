<template>
<div>
    <h1>Firebase</h1>

   
          <div v-if="t">
             <div v-for="i in l" :key="i">
                  <span>{{i}}</span>
          <button v-on:click="removeUser()" >X</button>
             </div>
          </div><br>
    

    <form action="">
        <input type="text"  id="" placeholder="Username" v-model="data.nom">
        <input type="email" name="" id="" placeholder="Email" v-model="data.email">
        <button type="submit" @click="addSubmit">Add User</button>
    </form>
    <ul class="errors">
        <li v-show="!data.nom">Name cannot be empty.</li>
        <li v-show="!data.email">
          Please provide a valid email address.
        </li>
      </ul>
</div>

    
</template>


<script>
export default {
    data () {
        
        return {
            l:[],
            data:{
                nom: "",
                email: ""
            },
            t : false
          
        }
    },
       methods: {
           addSubmit(){
               this.t = true
               this.l.push(this.data.nom+ " " + this.data.email)
         
            //    this.data.push(this.nom + " " + this.email)
            //    console.log(this.data)
           },
           removeUser(){
               this.t =false
           }
         
       }
}
</script>