<script setup>
import { computed } from 'vue';

 // review list container with code for handling the props

defineProps({
    reviews: {
        type: Array,
        required: true
    }
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
            </li>
        </ul>
    </div>
</template>
