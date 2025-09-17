<script setup>

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
    const amount = element[1].split(' ')[0]
    sum += parseInt(amount)
  });
  return sum
}

const rmItem = (summary, products, item) => {

  const name = item.split('\n')[0]
  const price = item.split('\n')[1]
  
  products.forEach((prod, index) => {
    console.log(prod)
    if (prod[0] == name && prod[1] == price) {
      console.log("rem")
      products.splice(index, 1)
      
      let amount = parseInt(summary[item])
      if (amount > 0) amount--
  
      summary[item] = amount;
      return
    }
  })
  
    
  
  
}

</script>

<template>
<div v-if="products.length > 0">
  <h3>Your cart:</h3>
  <div v-for="(index, item) in summary" :key="index" class="shopping-cart-item">
    <div v-if="summary[item] > 0">
    <h2>Product:</h2>
    <div class="cart-info">
    
      <h3>{{ item.split("\n")[0] }}</h3>
      <h4>{{ item.split("\n")[1] }}</h4>
      <div class="item-qty">
            <p>Quantity: {{ summary[item] }}</p>
            <button id="btn-minus" v-on:click="rmItem(summary, products, item)">-</button>
      </div>
    </div>
  </div>
</div>
  <p>TOTAL: {{ calculateSum(products) }} €</p>
</div>
<div v-else>
  <h3>Your cart is empty</h3>
</div>
</template>
