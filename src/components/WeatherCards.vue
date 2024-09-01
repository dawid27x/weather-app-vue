<script setup>
import WeatherForecastDay from './WeatherForecastDay.vue';

defineProps({
    place: Object

})
</script>
<template>
    <div class="text-white p-10 rounded-lg shadow-lg gap-6 mb-6 relative overflow-hidden bg-blue-800">
        <!-- Location and time -->
        <div class="mb-2 flex justify-between items-center gap-2">
        <div class="flex items-center justify-center gap-2">
            <i class="fa-solid fa-location-dit"></i>
            <h1 class="text-3xl">{{ place.location.name }}</h1>
        </div>
        <div class="flex items-center justify-center gap-2">
            <i class="fa-regular fa-clock"></i>
            <h1 class="text-3xl">{{ new Date (place.location.localtime).getHours() }}
            : {{ new Date (place.location.localtime).getMinutes() }}</h1>
        </div>
        </div>

    <!-- Current Weather -->
        <div class="text-center flex-1">
            <img :src="place.current.condition.icon" alt="icon" width="200"
            class="mx-auto -mb-30" />
            <h1 class="text-9xl mb-2 -mr-4">{{ Math.round(place.current.temp_c) }}&deg;</h1>
            <p class="text-2xl">{{ place.current.condition.text }}</p>
        </div>

        <br />
        <!-- Forecast -->
        <div v-for="(day, idx) in place.forecast.forecastday" :key="idx">
            <WeatherForecastDay :day="day" />
        </div>
        <!-- More -->
        <div>

        </div>

        <div class="flex justify-end items-center gap-1 mt-10">
            <button>More <i class="fa-solid fa-arrow-right text-sm -mb-px"></i> </button>
        </div>
    </div>
</template>