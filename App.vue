<script setup>
import {ref, computed} from 'vue';

const products = ref([
  {product: "Rijst", price: 1.00, amount: 0},
  {product: "Brocolli", price: 0.99, amount: 0},
  {product: "Koekjes", price: 1.20, amount: 0},
  {product: "Noten", price: 2.99, amount: 0}
])

const calculateTotal = computed(() => {
  return  products.value.reduce((sum, product) => sum + (product.price * product.amount), 0);
})

</script>

<template>
 <h1>Boodschappenlijst</h1>
 <table>
  <thead>
      <tr>
        <th>Product</th>
        <th>Prijs</th>
        <th>Aantal</th>
        <th>Totaal</th>
      </tr>    
  </thead>
  
  <tbody>
    <tr v-for="product in products" :key="product.product">
      <td>{{ product.product }}</td>
      <td>{{ product.price }}</td>
      <td><input v-model.number= "product.amount" type="number" placeholder="Amount" {{ product.amount }} min="0"></td>
      <td>{{ (product.price * product.amount).toFixed(2)}}</td> <!--To get the subtotal for each product-->
    </tr>
  </tbody>
 </table>
 <br>
 <h2>Totaal: {{ calculateTotal.toFixed(2) }}</h2>
</template>


