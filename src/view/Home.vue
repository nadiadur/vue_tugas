<template>
  <div class="flex flex-col p-8 item-center justify-center">
    <div>
     
    </div>

    <div class="flex justify-center gap-2 mt-2">
      <router-link
        :to="{ name: 'byLetter', params: { letter: letter } }"
        :key="letter"
        v-for="letter in letters"
      >
        {{ letter }}
      </router-link>
    </div>
   
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import store from "../store";
import axiosClient from "../axiosClient.js";

const meals = computed(() => store.state.meals);

const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const ingredients = ref([]);

onMounted(async () => {
  const response = await axiosClient.get('/list.php?i=list');
  console.log(response.data);
  ingredients.value = response.data;
});
</script>

<!-- Import lainnya atau template HTML lainnya dapat ditempatkan di sini -->


<style>
</style>