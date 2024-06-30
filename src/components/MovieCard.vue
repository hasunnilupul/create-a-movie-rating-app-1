<script setup>
import { StarIcon } from "@heroicons/vue/24/solid";
const props = defineProps({
    data: { type: Object, required: true }
});

const { id, name, description, image, rating, genres } = props.data;
</script>

<template>
    <div class="flex flex-col bg-white rounded-md">
        <div class="block h-96">
            <!-- Poster -->
            <img :src="image" :alt="name" class="w-full h-full rounded-t-md" />
        </div>
        <div class="flex flex-col h-full p-3">
            <!-- Title -->
            <h3 class="text-lg font-medium text-wrap line-clamp-2">{{ name }}</h3>
            <!-- Genres -->
            <div class="mt-1 flex flex-row flex-wrap space-x-1">
                <span v-for="genre in genres" :key="genre"
                    class="inline-flex items-center rounded-full bg-indigo-500 px-2 py-1 text-xs font-medium leading-none text-white">
                    {{ genre }}
                </span>
            </div>
            <!-- Description -->
            <p class="m-0 mt-2 text-xs font-medium text-gray-800">
                {{ description }}
            </p>
            <!-- Rating -->
            <div class="flex flex-row mt-auto pt-3">
                <p class="text-xs font-normal text-gray-800">
                    Rating: <span>({{ rating }}/5)</span>
                </p>
                <!-- Rating Stars -->
                <div class="ml-2.5 flex flex-row space-x-0.5">
                    <StarIcon v-for="rate in rating" :key="rate" class="w-4 h-4 text-yellow-500" />
                    <StarIcon v-for="rate in (5 - rating)" :key="rate" class="w-4 h-4 fill-white stroke-black" />
                </div>
            </div>
        </div>
    </div>
</template>