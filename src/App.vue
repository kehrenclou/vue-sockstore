<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = ref(true)

//used for example else-if example in template below
// const inventory =ref(8)

</script>

<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" />
        <!--v-bind shorthand is :  -->
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if=inStock>In Stock</p>
        <p v-else>OUt of Stock</p>

        <!-- this example demonstrates using else ifs -->
        <!-- <p v-if="inventory > 10">In Stock</p>
        <p v-else-if="inventory <=10 && inventory >0">Almost sold out!</p>
        <p v-else>Out of Stock</p> -->
      </div>
    </div>
  </div>
</template>
