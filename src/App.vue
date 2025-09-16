<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

import cat1 from '@/assets/images/cat1.jpg'
import cat2 from '@/assets/images/cat2.jpg'
import cat3 from '@/assets/images/cat3.jpg'
import cat4 from '@/assets/images/cat4.jpg'

const artworkTitles = ref(["A cat dreaming", "A cat in psychedelic room", "A wondering cat", "A cat in the dark"])

const c1 = ref("")
const c2 = ref("")
const c3 = ref("")
const c4 = ref("")

</script>

<template>
  <div class="nav-bar">
    <h1 id="htitle">Art Shop</h1>
  </div>
  
  <div class="products-container">
  <div class="products">
    <ProductDisplay :image=cat1 :condition="c1" :name=artworkTitles[0]></ProductDisplay>
    <ProductDisplay :image=cat2 :condition="c2" :name=artworkTitles[1]></ProductDisplay>
    <ProductDisplay :image=cat3 :condition="c3" :name=artworkTitles[2]></ProductDisplay>
    <ProductDisplay :image=cat4 :condition="c4" :name=artworkTitles[3]></ProductDisplay>
  </div>
  </div>
  
</template>