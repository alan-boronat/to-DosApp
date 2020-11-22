<!-- Componente creado para el manejo de eventos que ocurran sobre cada tarea, por ejemplo cuando se elimina o completa una tarea -->

<template>
    <div class="todo" v-bind:class="{completed: todo.completed}">
        <div class="todo-body" >
            <input type="checkbox" 
                v-bind:checked="todo.completed? 'checked': ''"
                v-on:change="checkTodo">
            {{todo.title}}
        </div>

        <div class="todo-actions">
            <button @click="$emit('delete-todo', todo.id)">Eliminar</button>
        </div>
    </div>   
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        checkTodo(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<!-- Propiedades de estilos CSS -->
<style scoped>
    .todo{
        border-bottom: solid 1px #ccc;
        padding: 10px;
        color: white;
    }

    .todo:not(.completed):hover{
        background-color:#236E96;
        
    }

    .completed{
        color: #ccc;
        text-decoration: line-through;
    }
    .completed .todo-body{
        text-decoration: line-through;
    }

    .todo-body, .todo-actions{
        display: inline-block;
        vertical-align: top;
    }

    .todo-body{
        width: 85%;
    }
    .todo-actions{
        padding: 0 10px;
        width: 10%;
    }

    button{
        border: none;
        border-radius: 3px;
        padding: 10px;
        background-color: white;
        color: black;
    }
    button:hover{
        background-color: #da2020;
        color: white;
    }
</style>