<script setup>
import { ref } from "vue";
import SearchInput from "./components/SearchInput.vue";
import WeatherCards from "./components/WeatherCards.vue";

const places = ref([]);

const addPlace = (data) => {
  places.value.push(data)
};
</script>
<template>
  <main>
    <!-- Date -->
    <div class="text-center mb-6">
      {{ new Date().toLocaleDateString('en-us',
        { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) }}
    </div>
    <!-- Search -->
    <div>
      <SearchInput @place-data="addPlace"/>
    </div>

    <!-- Weather cards -->
    <div class="grid grid-cols-3 gap-2">
      <div v-for="(place, idx) in places" :key="idx">
      <WeatherCards :place="place"/>
    </div>
    </div>
  </main>
</template>