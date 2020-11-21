<!-- Componente creado para listar todas las tareas recorriendo el arreglo de tareas "todoslist"  -->

<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todoslist">
            <TodoItem v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)" />
        </div>
    </div>
</template>

<script>
/* import { component } from 'vue/types/umd'; */
import TodoItem from './TodoItem';
export default {
    name: 'Todos',
    props: ['todoslist'],
    components: {TodoItem}
}
</script>

<style>

</style>