<template>
  <input
    type="text"
    class="rounded md:w-80 w-full"
    ref="textBox"
    placeholder="Type something..."
    v-model="inputText"
  />

  <div class="flex gap-3">
    <span
      v-for="each in getRandomCricketWords()"
      class="text-xs border rounded p-1 px-2 border-gray-700 hover:bg-gray-200 transition-colors cursor-pointer"
      @click="updateInputValue(each)"
      >{{ each }}</span
    >
  </div>

  <button
    type="button"
    v-if="getLetterCount() === 7"
    @click="updateParentData"
    class="text-gray-900 font-medium bg-white border border-gray-300 hover:bg-gray-100 rounded text-sm px-4 py-2"
  >
    Click to see magic!🎉
  </button>
  <p v-else class="text-gray-400 text-xs">
    Letter count: {{ getLetterCount() }}/7
  </p>
</template>

<script setup>
import { ref, inject, reactive } from "vue";

const total = ref(0);
const inputText = ref("");
const textBox = ref("textBox");

const getLetterCount = reactive(() => inputText.value.length);

const sharedData = inject("sharedData");

const updateParentData = () => {
  sharedData.value = total.value;
  localStorage.setItem("word", inputText.value);
};

const updateInputValue = (each) => {
  inputText.value = each;
};

function getRandomCricketWords() {
  const cricketWordsArray = [
    "batting",
    "bowling",
    "wickets",
    "captain",
    "snippet",
    "umpires",
    "cricket",
    "outdoor",
    "innings",
    "spinner",
  ];

  // Shuffle the array and get 3 random cricket-related words
  const shuffledArray = cricketWordsArray
    .slice()
    .sort(() => Math.random() - 0.5);
  const randomCricketWords = shuffledArray.slice(0, 3);

  return randomCricketWords;
}
</script>
