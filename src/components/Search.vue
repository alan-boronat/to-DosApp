<!-- Componente creado para buscar tareas en la lista, filtrando las palabras ingresadas mediante el metodo "querySearch" -->

<template>
    <div id="search-container">
        <input type="text" v-model="query" v-on:input="$emit('query-change', query)" placeholder="Puede buscar sus tareas aqui">
    </div>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return {
            query: ''
        }
    }
}
</script>

<!-- Propiedades de estilos CSS -->
<style scoped>
    #search-container{
        width: 600px;
        margin: 0 auto;
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