<script setup>
// Importando funcion
// para crear referencias reactivas
import { ref } from 'vue'
// Creando una referencia reactiva
// de tipo string
const header = ref ('App lista de compras');
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
//Metodos
const saveItems = () => {};
//Agrega un nuevo elemento a la lista 
//Proveniente de la caja de texto 
items.value.push({id: items.value.length, label: newItem.value})
//Borramos el contenido de la caja de texto 
newItem.value="";
</script>

<template> 
   <h1> <i :class="shoppingIcon">local_mall</i> <span v-html="bag"></span> {{ header }} </h1>
   <form v-on:submit.prevent="saveItems"
    class="Add-Item form">
      <input v-model="newItem" type="text" 
      placeholder="Agregar Articulo">
   <!-- Radio Button -->
      <label><input type="checkbox" v-model="newItemHighPriority">
         Alta prioridad</label>
      <!-- Button-->
      <button class="btn btn-primary">
      Agregar articulo</button>
</form>
   <ul>
    <li v-for="({id,label}, ) in items" v-bind:key="id">⭐ {{ label }}</li>
   </ul>
</template>
<style scoped>
</style>
