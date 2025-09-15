<script setup>
import { ref, computed } from 'vue'
import cat1 from '@/assets/images/cat1.jpg'
import cat2 from '@/assets/images/cat2.jpg'
import cat3 from '@/assets/images/cat3.jpg'
import cat4 from '@/assets/images/cat4.jpg'

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
        <img src="cat1">
      </div>
      
      </div>
    </div>

</template>