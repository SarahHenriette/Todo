<template>
<div>
    <h1>Firebase</h1>

   
          <div v-if="t" id="e">
             <div v-for="i in l" :key="i" class="i">
                  <span >{{i}}</span>
          <button v-on:click="removeUser(i)" >X</button>
             </div>
          </div><br>
    

    <form action="">
        <input type="text"  id="" placeholder="Username" v-model="data.nom">
        <input type="email" name="" id="" placeholder="Email" v-model="data.email">
        <button type="submit" @click="addSubmit">Add User</button>
    </form>
        <ul class="errors">
            <li v-show="!data.nom">Name cannot be empty.</li>
            <li v-show="!data.email">Please provide a valid email address.</li>
            <!-- <li v-if="data.test">ces donnees existes déjà</li> -->
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
                email: "",
                // test:false
            },
            t : false,
            close:true
          
        }
    },
       methods: {
           addSubmit(){
              
               this.t = true
               if(this.l.length === 0){
                    this.l.push(this.data.nom+ " " + this.data.email)
               }else{
                    this.l.forEach(element => {
                        if(element == this.data.nom+ " " + this.data.email){
                               console.log('Ces données existe déjà')
                        }else{
                            this.l.push(this.data.nom+ " " + this.data.email)

                        }
                    });
               }
               this.data.nom=""
               this.data.email=""
               
         
            //    this.data.push(this.nom + " " + this.email)
            //    console.log(this.data)
           },
           removeUser(user){
       
            var id = document.getElementById('e')
            var clas = id.getElementsByClassName('i')

            for (let index = 0; index < clas.length; index++) {
                if(clas[index].childNodes[0].innerText == user)
                clas[index].remove()
                
            }
         
              

               
           }
         
       }
}
</script>