<script setup>
  import { ref } from 'vue';

  import hoodieImage from './assets/images/Hoodie_1.png'

  const product = ref('Hoodie');
  const description = ref('A good looking hoodie for winter time 😎.')
  const inventory = ref(1);
  const onSale = ref(true);
  const details = ref(['80% cotton', '10% wool', '10% polyester']);
  const variants = ref([
  {id: 2222, color: 'black'},
  {id: 3333, color: 'red'}
  ]);
  const sizes = ref(['XS', 'S', 'M', 'L', 'XL','Lose some weight to fit in it!']);


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
      <p v-if="inventory > 10">In stock</p>
      <p v-else-if="inventory <= 10 && inventory > 0">Almost out of stock</p>
      <p v-else ="inventory = 0">Out of stock</p>
            <ul>
        <li v-for ="detail in details">{{ detail }}</li>
      </ul>
      <div v-for = "variant in variants" :key="variant.id">{{ variant.color }}</div>
      <hl>
        <li v-for="size in sizes">{{ size }}</li>
      </hl>
      <p v-if="onSale">On Sale!</p>

    </div>
  </div>
</div>
</template>

