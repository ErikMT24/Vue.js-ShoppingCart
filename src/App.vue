<script setup>
// Importando funcion
// para crear referencias reactivas
import { ref } from 'vue'
// Creando una referencia reactiva
// de tipo string
const header = ref (' App lista de compras');
//const bag = ref('<i class="material-icons shopping-cart-icon">local_mall</i>')
const shoppingIcon = ref('material-icons shopping-cart-icon');
//Creando una referencia reactiva
//para almacenar el valor de la lista 
const items = ref([ 
{id: 0, label:'Leche'},
{id: 2, label:'Arroz'},
{id: 3, label:'Carne'},
{id: 4, label:'Pan'}, 
{id: 5, label:'Huevos'}
]);
</script>

<template>
   <h1> <i :class="shoppingIcon">local_mall</i> <span v-html="bag"></span> {{ header }} </h1>
   <ul>
    <li v-for="({id,label}, i) in items" v-bind:key="id">⭐ {{ i }} {{ label }}</li>
   </ul>
</template>
<style scoped>
</style>
