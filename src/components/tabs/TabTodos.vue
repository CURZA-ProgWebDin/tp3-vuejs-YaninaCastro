<template>
      <ListaProductos :productos="productos"/>
</template>

<script setup>
import { productos } from '@/data/productos.js';
import ListaProductos from '../ListaProductos.vue';
import { onMounted, onUnmounted, onActivated, onDeactivated } from 'vue';

onMounted(()      => console.log('TabTodos — montado'))

onUnmounted(()    => console.log('TabTodos — desmontado'))

onActivated(()    => console.log('TabTodos — activado'))

onDeactivated(()  => console.log('TabTodos — desactivado'))


</script>