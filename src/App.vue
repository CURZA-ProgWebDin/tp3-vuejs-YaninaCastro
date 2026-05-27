<template>
<TarjetaProducto v-for="producto in productos" :key="producto.id">
    <template #header>{{ producto.nombre }}-{{ producto.categoria }}</template>
    <template #body="{expandida, toggleExpandir}">
        <button @click="toggleExpandir">{{ expandida ? 'Cerrar':'Ver más' }}</button>
        <p v-if="expandida">Este producto tiene información adicional disponible</p>
    </template>
</TarjetaProducto>
</template>

<script setup>
import TarjetaProducto from './components/TarjetaProducto.vue';
import { productos } from './data/productos.js';
</script>


