<script setup>
import { ref, reactive } from 'vue'

//setup uses composition API - think of it's equivalent as React Hooks 
//(hooks = Composables in Vue) start variable name with use


//initializing ref (like React state)
const product = ref('Socks') //ref is  equivalent to React state

//initializing reactive (alt state method) - intended for object type data
//use reactive if a lot of related data - group in same object
const rProduct = reactive({ name: 'RSocks' })


//using ref to set state in vue -- use for simple values
setTimeout(() => {
  product.value = 'New Socks' //  value property used for both read and write eq. to React [state,setState]
}, 1000)

//using reactive to set state in Vue - intended for object type data
setTimeout(() => {
  rProduct.name = 'New RSocks'
}, 2000)


</script>

<template>
  <!--initializing state with ref - you don't need .value-->
  <h1>{{ product }}</h1>

  <!-- {{ product }} equivalent to React {product}; no need to use .value as it is automatically added -->

  <!--initializing state with reactive - you need .name -->
  <h2>{{ rProduct.name }}</h2>


</template>
