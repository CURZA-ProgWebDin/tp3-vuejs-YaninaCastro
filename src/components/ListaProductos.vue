<template>
    <div ref="box" class="lista">
    <p v-if="cargando">Cargando...</p>
    <TarjetaProducto v-for="producto in productos" :key="producto.id">
        <template #header>Nombre: {{ producto.nombre }}- Categoría:{{ producto.categoria }}</template>
        <template #body="{expandida, toggleExpandir }">
            <button @click="toggleExpandir">{{ expandida ? 'Cerrar':'Ver más'}}</button>
            <p v-if="expandida"> Precio: ${{ producto.precio }}-Cantidad: {{ producto.stock }}</p>
        </template>
    </TarjetaProducto>
    </div>

</template>

<script setup>
import { onMounted, onUpdated, onBeforeUnmount } from 'vue';
import { ref, useTemplateRef } from 'vue';
import TarjetaProducto from './TarjetaProducto.vue';

const cargando = ref(false)
let timer = null
const props = defineProps ({
    productos:{
    type: Array,
    required: true
    }
})
const box = useTemplateRef('box')

function esperar(ms) {
  return new Promise(resolve => setTimeout(resolve, ms))
}

async function cargarProductos() {
    cargando.value = true
    if (cargando.value) {
        console.log('cargando...')
    }
    await esperar(800)
    cargando.value = false   
}

onMounted (() => {
    cargarProductos()
    timer = setInterval(() => {
        console.log('recargando productos')
        cargarProductos()
    }, 30000)

})

onUpdated(() => {
  if (box.value) {
    box.value.scrollTop = box.value.scrollHeight
  }
})

onBeforeUnmount (() => {
    clearInterval(timer)
    console.log('ListaProductos desmontado — polling detenido')
})

</script>

<style scoped>
.lista {
    max-height:400px;
    overflow-y: auto;
}
</style>