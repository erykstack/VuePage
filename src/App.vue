<script setup>
  import { ref } from 'vue';

  import hoodieImage from './assets/images/Hoodie_1.png'
  import hoodieImage2 from './assets/images/Hoodie_2.png'
  const product = ref('Hoodie');
  const image = ref(hoodieImage);
  const description = ref('A good looking hoodie for winter time 😎.')
  const inStock = ref(false);
  const onSale = ref(true);
  const details = ref(['80% cotton', '10% wool', '10% polyester']);
  const variants = ref([
  {id: 2222, color: 'rgb(88,88,101)', image: hoodieImage},
  {id: 3333, color: 'rgb(99,56,60)', image: hoodieImage2}
  ]);
  const sizes = ref(['XS', 'S', 'M', 'L', 'XL','Lose some weight to fit in it!']);

  const cart = ref(0);

const addToCart = () => cart.value += 1;
const removeFromCart = () => {
  if (cart.value >0)
  cart.value -= 1;
}

const updateImage = (variantImage) => image.value = variantImage
</script>

<template>
<div class="nav-bar"></div>
<div class="cart">Cart({{ cart }})</div>
<div class="product-display">
  <div class="product-container">
    <div class="product_image">
      <img :class="{ out_of_stock_img: !inStock }" v-bind:src="image">
    </div>
    <div class="product-info">
      <h1>{{ product }}</h1>
              <ul>
        <li v-for ="detail in details">{{ detail }}</li>
      </ul>
     <div v-for="variant in variants" 
          :key="variant.id"
          @mouseover="updateImage(variant.image)"
          class="color-circle"
          :style="{backgroundColor: variant.color}"
        >
    </div>
      <hl>
        <li v-for="size in sizes">{{ size }}</li>
      </hl>
      <p v-if="onSale">On Sale!</p>
      <button class="button" v-on:click="addToCart"
      :class="{ disabledButton : !inStock}"
      :disabled= "!inStock" 
      >Add to Cart</button> <!--instead of v-on:click we can use @click -->
      <button class="button" @click="removeFromCart">Remove Item</button> <!--instead of v-on:click we can use @click -->
    </div>
  </div>
</div>
</template>



