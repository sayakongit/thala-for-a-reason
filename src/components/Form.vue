<template>
  <input
    type="text"
    class="rounded md:w-80 w-full"
    placeholder="Type something..."
    v-model="inputText"
  />

  <button
    type="button"
    v-if="getLetterCount() === 7"
    @click="updateParentData"
    class="text-gray-900 font-medium bg-white border border-gray-300 hover:bg-gray-100 rounded text-sm px-4 py-2"
  >
    Click to see magic!🎉
  </button>
  <p v-else class="text-opacity-80 text-xs">
    Letter count: {{ getLetterCount() }}/7
  </p>
</template>

<script setup>
import { ref, inject, reactive } from "vue";

const total = ref(0);
const inputText = ref("");

const getLetterCount = reactive(() => inputText.value.length);

const sharedData = inject("sharedData");

const updateParentData = () => {
  sharedData.value = total.value;
};
</script>
