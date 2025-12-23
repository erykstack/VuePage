<script setup>  

  import { ref, computed} from 'vue';

  import hoodieImage from '@/assets/images/Hoodie_1.png' //import of images
  import hoodieImage2 from '@/assets/images/Hoodie_2.png'

    const props = defineProps({  //definition of composition of Props variable
        details: {
            type: Array,
            required: true
        }

    })



const updateVariant = (index) => {selectedVariant.value = index}

</script>

<template>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>   <!--Looping through details array passed as prop from parent component -->
        </ul>



</template>
