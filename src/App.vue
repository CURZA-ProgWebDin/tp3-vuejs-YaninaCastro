<template>
<ListaProductos :productos="productos"/>
</template>

<script setup>
import ListaProductos from './components/ListaProductos.vue';
import { productos } from './data/productos.js';


</script>


