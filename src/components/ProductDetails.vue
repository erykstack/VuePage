<script setup>  

  import { ref, computed} from 'vue';

  import hoodieImage from '@/assets/images/Hoodie_1.png'
  import hoodieImage2 from '@/assets/images/Hoodie_2.png'

    const props = defineProps({
        details: {
            type: Array,
            required: true
        }

    })



const updateVariant = (index) => {selectedVariant.value = index}

</script>

<template>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>



</template>