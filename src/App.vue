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
const newItem = ref('');
const newItemHighPriority = ref(false);
</script>

<template> 
   <h1> <i :class="shoppingIcon">local_mall</i> <span v-html="bag"></span> {{ header }} </h1>
   <div class="Add-Item form">
      <input v-model="newItem" placeholder="Agregar Articulo">
   <!-- Radio Button -->
      <label><input type="checkbox" v-model="newItemHighPriority">Alta prioridad</label>
      <!-- Button -->
      <button class="btn btn-primary" v-on:click="items.push({id: items.length, label:newItem})">
         Agregar Articulo</button>
   </div>
   <ul>
    <li v-for="({id,label}, i) in items" v-bind:key="id">⭐ {{ i }} {{ label }}</li>
   </ul>
</template>
<style scoped>
</style>
