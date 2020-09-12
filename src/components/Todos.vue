<template>
    <section class="todoapp">
        <header class="header">
            <h1>To do</h1>
            <input type="text" class="new-todo" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter="addTodo" >
        </header>
        <div class="main">
            <input type="checkbox" class="toggle-all" v-model="allDone">
            <label for="toggle-all"></label>
            <ul class="todo-list">
                <li class="todo " v-for="todo in filteredTodos" v-bind:key="todo.name"  :class="{completed : todo.completed, editing: todo === editing}">
                    <div class="view">
                        <input for="i" type="checkbox" v-model="todo.completed" class="toggle" >
                        <label  @dblclick="editTodo(todo)" >{{ todo.name }}</label>
                        <button class="destroy" @click.prevent="deleteTodo(todo)"></button>
                    </div>
                    <input type="text" name="i" class="edit"  v-model="name"  @keyup.enter="doneEdit(todo)">
                </li>
            </ul>
        </div>
        <footer class="footer" v-show = "hasTodos">
            <span class="todo-count"><strong>{{ remaining }}</strong> tâche à faire</span>
            <ul class="filters">
                <li><a href="#" :class="{selected: filter === 'all'}" @click.prevent="filter = 'all'">Toutes</a></li>
                <li><a href="#" :class="{selected: filter === 'todo'}" @click="filter = 'todo'">A faire</a></li>
                <li><a href="#" :class="{selected: filter === 'done'}" @click.prevent="filter = 'done'">Faites</a></li>
                <button class="cler-completed" @click.prevent="deleteCompleted" v-show="completed">Supprimer </button>

            </ul>
        </footer>
    </section>
</template>
    

<script>
import Vue from 'vue'

export default {
    data () {
        
        return {
            todos: [{
                name: 'tache de test', 
                completed: false,
            }],
            newTodo: '',
            filter: 'all',
            editing: null,
            name:''
        }
    },

    methods: {
        addTodo(){
            this.todos.push({
                completed: false,
                name: this.newTodo,
            })
            this.newTodo=''
        },

        deleteTodo(todo){
            this.todos=this.todos.filter(i=>i!== todo)
        },

        deleteCompleted(){
            this.todos = this.todos.filter(todo=>!todo.completed)
        },

        editTodo(todo){
          /**   this.name = todo.*/
          this.name = todo.name
            this.editing = todo
        },
        doneEdit(todo){
            todo.name= this.name
            this.editing= null
        }
    },

    computed: {
        remaining(){
            return this.todos.filter(todo => !todo.completed).length
        },

        completed(){
            return this.todos.filter(todo=>todo.completed).length
        },

        hasTodos(){
            return this.todos.length > 0
        },

        filteredTodos(){
            console.log("okk")
            if(this.filter === 'todo'){
                return this.todos.filter(todo =>!todo.completed)

            }else if(this.filter === 'done'){
                return this.todos.filter(todo => todo.completed)    
            }
            return this.todos
        },

        allDone:{

            get () {
                return this.remaining === 0
            },

            set (value) {
                console.log('value', value)
                this.todos.forEach(todo => {
                    todo.completed = value
                })
            }
        }
    },

      directives: {
        

           focus(el, value) {
                        console.log(el)

                if(value){
                        console.log(el)
                 let i =el;
                    Vue.nextTick(function(i){
                        console.log(i)

                        console.log(value)
                    })
                }
            }
        },

        

}


</script>


<style src="./todos.css"></style>