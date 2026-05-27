<template>
<div class="header"><slot name="header"></slot></div>
<div class="body"><slot name="body" :expandida="expandida" 
    :toggleExpandir="toggleExpandir"></slot></div>
<div class="footer"><slot name="footer">
    <span>Sin acciones disponibles</span>
</slot></div>
</template>

<script setup>
import { ref } from 'vue';
const expandida= ref("false")
function toggleExpandir () {
    expandida.value =! expandida.value
}

</script>

<style>
.tarjeta {
  border: 1px solid #ccc;
  padding: 12px;
  margin: 10px 0;
  border-radius: 8px;
}
</style>