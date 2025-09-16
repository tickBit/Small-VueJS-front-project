<script setup>

const props = defineProps({
  products: {
    type: Object,
    required: true
  }
})

</script>



<template>
  <h3>Your cart:</h3>
  <div v-for="(index, item) in products" :key="index" class="shopping-cart-item">
    <h3>Product:</h3>
    <h4>{{ item.split("\n")[0] }}</h4>
    <h5>{{ item.split("\n")[1] }}</h5>
    <p>Quantity: {{ products[item] }}</p>
  </div>
</template>
