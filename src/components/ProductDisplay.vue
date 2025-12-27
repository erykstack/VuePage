<script setup>  

  import { ref, computed} from 'vue';
  import hoodieImage from '@/assets/images/Hoodie_1.png'
  import hoodieImage2 from '@/assets/images/Hoodie_2.png'
    import ProductDetails from './ProductDetails.vue';
    import ReviewForm from './ReviewForm.vue';
    import ReviewList from './ReviewList.vue';

    const props = defineProps({ //function for checking the premium membership 
        premium: {
            type: Boolean,
            required: true
        }

    })
    const emit = defineEmits(['add-to-cart','remove-cart']); // Emitting event to parent component

  const product = ref('Hoodie');
  const brand = ref('Winter Collection');

  const selectedVariant = ref(0);

  const description = ref('A good looking hoodie for winter time 😎.')
  const details = ref(['80% cotton', '10% wool', '10% polyester']);
  const variants = ref([
  {id: 2222, color: 'rgb(88,88,101)', image: hoodieImage, quantity: 69},
  {id: 3333, color: 'rgb(99,56,60)', image: hoodieImage2, quantity: 2}
  ]);
  const sizes = ref(['XS', 'S', 'M', 'L', 'XL','Lose some weight to fit in it!']);

  const tittle = computed(() => {
    return brand.value + ' ' + product.value;
  })

const reviews = ref([]); // Array to hold reviews submitted from ReviewForm component

const lastRecommend = ref(null); // Variable to hold the last recommend value


const addToCart = () => { // Function to emit event to parent component from button click
    emit('add-to-cart', variants.value[selectedVariant.value].id);
}

const removeFromCart = () => { // Function to emit event to parent component from button click
    emit('remove-cart');
}

const image = computed (() => { //change the property of image based on selected variant
  return variants.value[selectedVariant.value].image; 
})

const inStock = computed (() => {
  return variants.value[selectedVariant.value].quantity > 0; //checking the stock based on selected variant
})

const shipping = computed (() => {  //using Props for checking the premium user
    if(props.premium){
        return 'Free';
    }
    else {
        return '5€';
    }

})



const addReview = (review) => { reviews.value.push(review)
} // Function to add review to reviews array when review-submitted event is emitted from ReviewForm component

const updateVariant = (index) => {selectedVariant.value = index}

</script>

<template>
   
   <div class="product-display">
    <div class="product-container">
      <div class="product_image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ tittle}}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ProductDetails :details="details">  </ProductDetails>
        <p>Shipping: {{ shipping }}</p>
      
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

        <button
          class="button" 
          v-on:click="removeFromCart"
        >
          Remove item
        </button>
    
      </div>
    </div>
    <ReviewForm @review-submitted="addReview"></ReviewForm>
    <ReviewList v-if= "reviews.length > 0" :reviews="reviews"></ReviewList>
      
  </div>

</template>
