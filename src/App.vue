<script setup>

  import { ref} from 'vue';
  import ProductDisplay from '@/components/ProductDisplay.vue';
import ProductDetails from './components/ProductDetails.vue';

  const cart = ref([]);
  const premium = ref(false);
  const updateCart = (id) => {
    cart.value.push(id);
  }
const removeFromCart = () => {
  if (cart.value.length >0)
  cart.value.pop();
}


</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium ="premium" @add-to-cart="updateCart" @remove-cart="removeFromCart">  </ProductDisplay>

</template>

