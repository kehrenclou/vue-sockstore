<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from '../assets/images/socks_green.jpeg'
import socksBlueImage from '../assets/images/socks_blue.jpeg'

const props = defineProps({
  premium: {
    type: Boolean,
    required: true
  }
})

const product = ref('Socks')
const brand = ref('Vue Mastery')
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 }
])

const selectedVariant = ref(0)

const title = computed(() => {
  return brand.value + ' ' + product.value
})

const image = computed(() => {
  return variants.value[selectedVariant.value].image
})
const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const shipping = computed(() => {
  if (props.premium) {
    return 'Free'
  } else {
    return 2.99
  }
})

const addToCart = () => (cart.value += 1)
const updateVariant = (index) => {
  selectedVariant.value = index
}
</script>
<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" />
        <!--v-bind shorthand is :  -->
      </div>
      <div class="product-info">
        <h1>{{ title }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <p>Shipping: {{ shipping }}</p>
        <ul>
          <li v-for="detail in details" :key="detail.id">{{ detail }}</li>
        </ul>
        <div
          v-for="(variant, index) in variants"
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        ></div>

        <button
          class="button"
          :class="{ disabledButton: !inStock }"
          v-on:click="addToCart"
          :disabled="!inStock"
        >
          Add to Cart
        </button>
      </div>
    </div>
  </div>
</template>
