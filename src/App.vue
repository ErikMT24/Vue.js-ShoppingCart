<script setup>
// Importando funcion
// para crear referencias reactivas
import { ref } from 'vue'
// import IconTooling from './components/icons/IconTooling.vue';
// Creando una referencia reactiva
// de tipo string
const header = ref ('App lista de compras')
const shoppingIcon = ref('material-icons shopping-cart-icon');
//Creando una referencia reactiva
//para almacenar el valor de la lista 
 const items = ref([ 
// {id: 0, label:'Leche', purchased: false, highPriority: true},
// {id: 2, label:'Arroz', purchased: false, highPriority: false},
// {id: 3, label:'Carne', purchased: true, highPriority: false},
// {id: 4, label:'Pan', purchased: false, highPriority: false}, 
// {id: 5, label:'Huevos', purchased: true, highPriority: true}
]);
const togglePurchased = (item) => {
   item.purchased = !item.purchased
};
const newItem = ref('')
const newItemHighPriority = ref(false);

const saveItems = () => {
//Agrega un nuevo elemento a la lista 
//Proveniente de la caja de texto 
items.value.push(
   {
      id: items.value.length, label: newItem.value,
      highPriority: newItemHighPriority.value
   })
//Borramos el contenido de la caja de texto 
newItem.value="";
newItemHighPriority.value = false;
};
//Paso 2
const doEdit = (edit) => {
   showAddItem.value = edit;
   newItem.value = "";
   newItemHighPriority.value = false; 
}
//Paso 1 para la visualizacion
const showAddItem = ref(false);
</script>

<template> 
<!-- Header -->
<div class="header">
   <h1>
       <i :class="shoppingIcon">local_mall</i> <span v-html="bag"></span> {{ header }} 
      </h1>
      <button
      v-on:click="doEdit(false)"
       v-if="showAddItem" class="btn">Cancelar</button>
      <button
       v-else
       v-on:click="doEdit(true)"
        class="btn btn-primary">Agregar articulo
      </button>
</div>
      <!-- Formulario -->
   <form v-if="showAddItem" v-on:submit.prevent="saveItems"
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
<!-- Entrega de lista  -->
   <ul>
    <li v-for="({id,label, purchased, highPriority}, index) in items" 
    @click="togglePurchased(items[index])"
    :class= "{priority: highPriority, strikeout :purchased}"
    v-bind:key="id">⭐{{ label }}</li>
   </ul>
   <!-- <ul>
    <li v-for="({id,label, purchased, highPriority}, ) in items" 
    :class= "[purchased ? 'strikeout': '', highPriority ? 'priority': '']"
    v-bind:key="id">⭐{{ label }}</li>
   </ul> -->
   <!-- Mensaje condicional  -->
   <p v-if="items.length === 0">No hay elementos en la lista 🚫</p>   
</template>

<style scoped>
.shopping-cart-icon{
   font-size: 2rem;
}
</style>
