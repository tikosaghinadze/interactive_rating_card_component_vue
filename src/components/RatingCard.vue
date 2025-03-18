<script setup>
import { ref, defineEmits, defineProps } from "vue";
const props = defineProps({
  ratingNumbers: Array,
});

const emit = defineEmits(["rating-number", "submit"]);
const selectedRating = ref(null);

const chooseRating = (ratingNumber) => {
  selectedRating.value = ratingNumber;
  emit("rating-number", ratingNumber);
};
</script>
<template>
  <main
    class="p-8 w-[412px] bg-[radial-gradient(circle,_#232a34_0%,_#181e27_100%)] rounded-[30px]"
  >
    <img
      class="bg-[#262E38] p-4 rounded-full"
      src="../assets/starIcon.svg"
      alt="star icon"
    />
    <div>
      <h1 class="text-white text-[28px] font-bold mt-[30px] mb-[7px]">
        How did we do?
      </h1>
      <p class="text-[#969FAD] text-[15px] font-light">
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </p>
    </div>
    <ul class="flex gap-5 mt-6 justify-between">
      <li
        v-for="(ratingNumber, index) in ratingNumbers"
        :key="index"
        @click="chooseRating(ratingNumber)"
        :class="[
          selectedRating === ratingNumber
            ? 'bg-white text-[#262E38]'
            : 'bg-[#262E38] text-[#969FAD] hover:bg-[#FC7614] hover:text-white',
          'rounded-full w-[51px] h-[51px] flex justify-center items-center duration-300',
        ]"
      >
        {{ ratingNumber }}
      </li>
    </ul>
    <button
      @click="emit('submit')"
      class="bg-[#FC7614] hover:bg-white duration-300 text-[#131518] w-full py-[15px] rounded-[50px] mt-8 uppercase font-bold border-none"
    >
      submit
    </button>
  </main>
</template>
