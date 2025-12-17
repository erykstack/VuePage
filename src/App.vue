<script setup>
  import { ref, computed} from 'vue';

  import hoodieImage from './assets/images/Hoodie_1.png'
  import hoodieImage2 from './assets/images/Hoodie_2.png'
  const product = ref('Hoodie');
  const brand = ref('Winter Collection');

  const selectedVariant = ref(0);

  const description = ref('A good looking hoodie for winter time 😎.')

  const onSale = ref(true);
  const Sale = computed(() => {
    if (onSale.value){
      return ' product is on Sale!';
    }
    else return '';
  })

  const details = ref(['80% cotton', '10% wool', '10% polyester']);
  const variants = ref([
  {id: 2222, color: 'rgb(88,88,101)', image: hoodieImage, quantity: 69},
  {id: 3333, color: 'rgb(99,56,60)', image: hoodieImage2, quantity: 0}
  ]);
  const sizes = ref(['XS', 'S', 'M', 'L', 'XL','Lose some weight to fit in it!']);

  const cart = ref(0);

  const tittle = computed(() => {
    return brand.value + ' ' + product.value;
  })

const addToCart = () => cart.value += 1;
const removeFromCart = () => {
  if (cart.value >0)
  cart.value -= 1;
}

const image = computed (() => {
  return variants.value[selectedVariant.value].image; 
})

const inStock = computed (() => {
  return variants.value[selectedVariant.value].quantity > 0;
})

const updateVariant = (index) => {selectedVariant.value = index}
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product_image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ tittle + Sale}}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div 
          v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        >
        </div>
        <button
          class="button" 
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>

