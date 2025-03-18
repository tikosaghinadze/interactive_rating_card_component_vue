<script setup>
import { ref } from "vue";
import RatingCard from "./components/RatingCard.vue";
import ResponseCard from "./components/ResponseCard.vue";
const ratingNumbers = [1, 2, 3, 4, 5];
const chooseRating = ref(0);
const showResponse = ref(false);

const handleSubmit = () => {
  if (chooseRating.value !== 0) {
    showResponse.value = true;
  }
};
</script>

<template>
  <RatingCard
    v-if="!showResponse"
    @rating-number="chooseRating = $event"
    :ratingNumbers="ratingNumbers"
    @submit="handleSubmit"
  />
  <ResponseCard v-else :ratingNumber="chooseRating" />
</template>
