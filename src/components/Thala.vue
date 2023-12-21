<template>
  <img src="../assets/thala.gif" alt="" />
  <p class="text-2xl">Yayy! Thala For a Reason 😤</p>
  <audio ref="audioPlayer">
    <source :src="songUrl" type="audio/mpeg" />
  </audio>

  <a href="/" class="text-gray-900 font-medium bg-white border border-gray-300 hover:bg-gray-100 rounded text-sm px-4 py-2">Try Again</a>
</template>

<script setup>
import { onMounted, ref } from "vue";
import songUrl from "../assets/boleJoKoyal.mp3";
const audioPlayer = ref(null);

onMounted(() => {
  console.log("myheader mounted");

  console.log(audioPlayer.value);

  // Play the song
  audioPlayer.value?.play();
});
</script>
