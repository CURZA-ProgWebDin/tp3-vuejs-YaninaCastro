<template >
      <ListaProductos :productos="productosPerificos"/>

</template>

<script setup>
import { productos } from '@/data/productos.js';
import ListaProductos from '../ListaProductos.vue';
import { computed } from 'vue';
import { onMounted, onUnmounted, onActivated, onDeactivated } from 'vue';

const productosPerificos = computed (() =>
    productos.filter ( producto => producto.categoria === 'Periféricos')
)

onMounted(()      => console.log('TabPerifericos — montado'))

onUnmounted(()    => console.log('TabPerifericos — desmontado'))

onActivated(()    => console.log('TabPerifericos — activado'))

onDeactivated(()  => console.log('TabPerifericos — desactivado'))

</script>