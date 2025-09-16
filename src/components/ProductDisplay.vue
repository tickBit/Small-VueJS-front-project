<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  image: {
    type: String,
    required: true
  },
  condition: {
    type: String,
    required: true
  },
  name: {
    type: String,
    required: true
  },
})

const emit = defineEmits(['add-to-cart'])

const selection = ref("")

const variants = ref([
  { id: 1, cond: "New", price: '100 €' },
  { id: 2, cond: "Used", price: '15 €' }
])

const selectedVariant = computed(() =>
  variants.value.find(v => v.id === Number(selection.value))
)

const addToCart = (name, price) => {
  emit('add-to-cart', name, price)
}

</script>

<template>
  <div class="product-display">
    <div class="product-container">
    
      <div class="product-image">
      <h3>{{ name }}</h3>
        <img :src="image" alt="Product Image" />
          <div v-for="val in variants" :key="condition + val.id">
            <input :id="condition + val.id" type="radio" :name="condition" :value="val.id" v-model="selection" />
            <label :for="condition + val.id">Condition: {{ val.cond }}</label>
          </div>
          <div v-if="selectedVariant">
            <label>Price: {{ selectedVariant.price }}</label>
          </div>
      
            <button v-if=(selection) class="btn-buy" v-on:click="addToCart(name, selectedVariant.price)">Buy</button>
      </div>
    </div>
  </div>

</template>