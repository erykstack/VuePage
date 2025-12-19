<script setup>

  import { ref} from 'vue';
  import ProductDisplay from '@/components/ProductDisplay.vue';
  import ProductDetails from './components/ProductDetails.vue';

  const cart = ref([]); // Array to hold cart items with ids
  const premium = ref(false); // Boolean to indicate if user is premium
  const updateCart = (id) => {  // Function to update cart when event is received from child component
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

