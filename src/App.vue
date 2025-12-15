<script setup>
  import { ref } from 'vue';

  import hoodieImage from './assets/images/Hoodie_1.png'

  const product = ref('Hoodie');
  const description = ref('A good looking hoodie for winter time 😎.')
</script>

<template>
<div class="nav-bar"></div>
<div class="product-display">
  <div class="product-container">
    <div class="product_image">
      <img v-bind:src="hoodieImage">
    </div>
    <div class="product-info">
      <h1>{{ product }}</h1>
      <p>{{ description }}</p>
    </div>
  </div>
</div>
</template>

