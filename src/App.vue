<!-- Componente principal creado para renderizar todo el contenido de la app -->


<template>
  <div>
    
      <div>
        
        <Header />
    </div>
    <div id="main-container">
      <h2>Organizador De Tareas Web  <img src="./assets/task32.png"></h2>
      <Search v-on:query-change="querySearch" />
      <TodoAdd v-on:add-todo="addTodo" />
      <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />  
    </div>
    
  </div>
</template>

<script>
/* Importacion de componentes para renderizar  */
import Search from './components/Search'
import Todos from './components/Todos'
import TodoAdd from './components/TodoAdd'
import Header from './components/Header'


/* Se indican los componentes que van a renderizarse */
export default {
  name: 'App',
  components: {
     Todos, TodoAdd, Search, Header
    
  },
  
  /* Se crean los metodos que definiran el comportamiento de los componentes  */
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [ ... this.todos];
    },
    addTodo(todo){
    this.todos.push(todo);
    this.copyTodos = [ ... this.todos];
    },
  
  querySearch(query){
      if(query.trim() === ''){
        this.copyTodos = [...this.todos];
      }else{
        const temp = this.todos.filter(todo =>{
          return todo.title.includes(query)
        });

        this.copyTodos = [...temp];
      }
    }
  },
  
  /* Se crea una lista estática con tareas de ejemplo */
  data(){
    return{
      todos: [
      {
        id: 0,
        title: 'tarea completada',
        completed: true
      },
      {
        id: 1,
        title: 'tarea pendiente',
        completed: false
      },
      {
        id: 2,
        title: 'organizar proyectos',
        completed: false
      }
      
    ],
    copyTodos: [],      
    }
  },
  created(){
    this.copyTodos = [ ... this.todos]
  }
}
</script>


<!-- Propiedades de estilos CSS -->
<style>
  *{
    box-sizing: border-box;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5em;
    padding: 0;
    margin: 0;
    height: 100vh;

  background-color:#15B2D3 ;

  }
  

  #main-container{
    border: solid 1px #ccc;
    width: 600px;
    margin: 100px auto;
  }

  
  h2{
    text-align: center;
    color: white;
  }

  
</style>

