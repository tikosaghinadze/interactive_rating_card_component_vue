<script setup>
import { ref } from "vue";
import RatingCard from "./components/RatingCard.vue";
import ResponseCard from "./components/ResponseCard.vue";
const ratingNumbers = [1, 2, 3, 4, 5];
const chooseRating = ref(0);
</script>

<template>
  <RatingCard :ratingNumbers="ratingNumbers" :chooseRating="chooseRating" />
  <!-- <ResponseCard /> -->
</template>
