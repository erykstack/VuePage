<script setup>
import { computed } from 'vue';

 

defineProps({
    reviews: {
        type: Array,
        required: true
    }
})

const recommendText = computed (() => {
    return review.recommend === true 
    ? 'Would recommend' 
    : review.recommend === false 
    ? 'Would not recommend' : '';
})

</script>

<template>
    <div class="review-container">
        <h3>Reviews:</h3>
        <p></p>
        <ul>
            <li v-for = "(review, index) in reviews" :key="index">
                <span>{{ review.name }} gave this {{ review.rating }} ⭐️</span>
                <br/>
                <span>"{{ review.content }}"</span>
                <br/>
                <span> {{ recommendText }}</span>
            </li>
        </ul>
    </div>
</template>