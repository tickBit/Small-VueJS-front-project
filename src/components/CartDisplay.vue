<script setup>
import { computed } from 'vue';


const props = defineProps({
  summary: {
    type: Object,
    required: true
  },
  products: {
    type: Array,
    required: true
  }
})

const calculateSum = (products) => {
  
  let sum = 0;
  
  products.forEach(element => {
    const amount = element[1].split(" ")[0]
    sum += parseInt(amount)
  });
  return sum
}


</script>



<template>
  <h3>Your cart:</h3>
  <div v-for="(index, item) in summary" :key="index" class="shopping-cart-item">
    <h2>Product:</h2>
    <div class="cart-info">
      <h3>{{ item.split("\n")[0] }}</h3>
      <h4>{{ item.split("\n")[1] }}</h4>
      <p>Quantity: {{ summary[item] }}</p>
    </div>
  </div>
  <p>TOTAL: {{ calculateSum(products) }} €</p>
</template>
