<template>
  <Header />

  <!-- <p>The value: {{ check }}</p> -->

  <div class="flex flex-col gap-4 justify-center items-center py-10 px-5">
    <Form v-if="check === 7" />
    <Thala v-else />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Thala from "./components/Thala.vue";
import { ref, provide } from "vue";

const check = ref(7);

// Provide the property to child components
provide("sharedData", check);
</script>
