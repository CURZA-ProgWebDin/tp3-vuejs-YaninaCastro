<template >
      <ListaProductos :productos="productosElectronicos"/>

</template>

<script setup>
import { productos } from '@/data/productos.js';
import ListaProductos from '../ListaProductos.vue';
import { computed } from 'vue';
import { onMounted, onUnmounted, onActivated, onDeactivated } from 'vue';

const productosElectronicos = computed (() =>
    productos.filter ( producto => producto.categoria === 'Electrónica')
)

onMounted(()      => console.log('TabElectronico — montado'))

onUnmounted(()    => console.log('TabElectronico — desmontado'))

onActivated(()    => console.log('TabElectronico — activado'))

onDeactivated(()  => console.log('TabElectronico — desactivado'))

</script>