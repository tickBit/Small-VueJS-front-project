<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  image: {
    type: String,
    required: true
  }
})

const product = ref('Artwork')

const selectedVariant = ref(0)

const variants = ref([
  { id: 10, used: false, price: '100 €' },
  { id: 11, used: true, price: '15 €' }
])

const price = computed(() => {
  return variants.value[selectedVariant.used].price
})

const updateVariant = (index) => {
  selectedVariant.value = index
}

</script>

<template>
  <div class="product-display">
    <div class="product-container">
    
      <div class="product-image">    
        <img :src="image" alt="Product Image" />
      </div>
      
      </div>
    </div>

</template>