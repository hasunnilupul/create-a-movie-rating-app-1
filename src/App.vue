<script setup>
import { reactive } from "vue";

import { items } from "@/movies.json";
import MovieCard from "@/components/MovieCard.vue";

const movies = reactive({ ...items });
</script>

<template>
  <div class="flex h-screen w-screen items-center justify-center">
    <div class="m-14 grid grid-cols-3 gap-2 md:gap-3">
      <movie-card v-for="movie in movies" :key="movie.name" :data="movie" />
    </div>
  </div>
</template>
