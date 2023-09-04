<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

const premium = ref(true)
const cart = ref(0)
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <ProductDisplay :premium="premium"></ProductDisplay>
</template>
