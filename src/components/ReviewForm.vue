<script setup> 
import { reactive } from 'vue'

const emit = defineEmits (['review-submitted'])

const review = reactive ({ //description of review constant that is used for Product Review
    name: '',
    content: '',
    rating: null,
    recommend: ''
})

const onSubmit = () => {

    if(review.name === '' || review.content === '' || review.rating === null || review.recommend === null){
        alert('Please fill the form before sumbiting.')
        return;
    }

    const productReview = {
        name: review.name,
        content: review.content,
        rating: review.rating,
        recommend: review.recommend
    }


emit('review-submitted', productReview)

review.name = '';
review.content = '';
review.rating = null;
review.recommend = '';
}
</script>

<template>
    <form class = "review_form" @submit.prevent = "onSubmit">
        <h3>Leave a review</h3>
        <label for="name">Name:</label>
        <input id = "name" v-model="review.name">
        
        <label for = "review">Review:</label>
        <textarea id = "review" v-model="review.content"></textarea>
        <label for = "rating">Rating:</label>
        <select id = "rating" v-model.number = "review.rating">
            <option>5</option>
            <option>4</option>
            <option>3</option>
            <option>2</option>
            <option>1</option>  
        </select>
        <br/>
        <label for ="recomend">Would you recommend this item?</label>
        <select id ="recomend" v-model.recommend = "review.recommend">
            <option>Yes</option>
            <option>No</option>

        </select>

        <input class = "button" type="submit" value="Submit">
    </form>
</template>
