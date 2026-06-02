<template>
    <button @click="tabActivo = 'todos'">Todos</button>
    <button @click="tabActivo = 'electronicos'">Electrónica</button>
    <button @click="tabActivo = 'perifericos'">Periféricos</button>

    <h3>sin KeepAlive</h3>
    <component :is="tabs[tabActivo]"></component>

    <h3>con KeepAlive</h3>
    <keep-alive>
         <component :is="tabs[tabActivo]"></component>
    </keep-alive>

</template>

<script setup>
import TabTodos from './components/tabs/TabTodos.vue';
import TabPerifericos from './components/tabs/TabPerifericos.vue';
import TabElectronica from './components/tabs/TabElectronica.vue';
import { ref } from 'vue';

const tabs = {
    todos: TabTodos,
    electronicos: TabElectronica,
    perifericos: TabPerifericos
}

const tabActivo = ref('todos')



</script>