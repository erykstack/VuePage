<script setup>
import { computed } from 'vue';

 // review list container with code for handling the props

defineProps({
    reviews: {
        type: Array,
        required: true
    }
})

const recommendText = computed (() => { // Computed property to return recommendation text based on review data
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
