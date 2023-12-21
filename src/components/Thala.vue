<template>
  <img src="../assets/thala.gif" alt="" />
  <p>{{ getWord() }} = 7</p>
  <p class="text-2xl text-center">Yayy! Thala For a Reason 😤</p>
  <audio ref="audioPlayer">
    <source :src="songUrl" type="audio/mpeg" />
  </audio>

  <a
    href="/"
    class="text-gray-900 font-medium bg-white border border-gray-300 hover:bg-gray-100 rounded text-sm px-4 py-2"
    >Try Again</a
  >
</template>

<script setup>
import { onMounted, ref } from "vue";
import songUrl from "../assets/boleJoKoyal.mp3";
const audioPlayer = ref(null);
const word = ref("");

const getWord = () => {
  let arr = word.value.split("");
  arr = arr.join("+");
  return arr;
};

onMounted(() => {
  word.value = localStorage.getItem("word");
  // Play the song
  audioPlayer.value?.play();
});
</script>
