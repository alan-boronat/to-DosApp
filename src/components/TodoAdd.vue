<!-- Componente creado para agregar una nueva tarea a la lista mediante el metodo "addTodo" -->

<template>
    <div id="add-container">
        <form @submit="addTodo">
            <input type="text" v-model="title" placeholder="Ingrese una nueva tarea y presione enter para guardarla" required>
        </form>
    </div>
</template>

<script>
import { uuid } from 'vue-uuid';
export default {
    name: 'TodoAdd',
    data(){
        return {
            title: ''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();

            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.title = '';
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>

<!-- Propiedades de estilos CSS -->
<style scoped>
    #add-container{
        padding: 10px;
    }
    input{
        padding: 10px;
        outline: none;
        border: solid 1px #ccc;
        width: 100%;
        border-radius: 3px;
    }
</style>