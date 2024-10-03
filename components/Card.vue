<template>
  <div>
    <div :class="input ? 'mb-4' : 'mb-[3.75rem]'">
      <form class="max-w-md mx-auto">
        <label
          for="default-search"
          class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white"
          >Search</label
        >
        <div class="relative">
          <div
            class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none"
          ></div>
          <button
            v-if="input"
            @click="handleClear()"
            type="button"
            class="absolute end-2.5 bottom-2.5 rounded-full p-1 dark:text-gray-400 text-gray-600 dark:hover:text-white hover:text-black focus:outline-none focus:ring-2 dark:focus:ring-white focus:ring-black focus:ring-offset-2 dark:focus:ring-offset-gray-800 focus:ring-offset-gray-200"
          >
            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
          </button>
          <input
            type="search"
            v-model="input"
            id="default-search"
            class="block w-full p-4 ps-6 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="Encontre obras por título, autor, país ou data..."
          />
        </div>
      </form>
    </div>
    <div class="" v-for="artwork in filteredList()" :key="artwork._id"></div>
    <div class="h-full" v-if="input && !filteredList().length">
      <p class="text-xl text-center text-black dark:text-white">
        Nenhum resultado encontrado!
      </p>
    </div>
    <div class="h-full" v-if="input && filteredList().length">
      <p class="text-lg text-center text-black dark:text-white mb-4">
        {{ filteredList().length }} obras encontradas
      </p>
    </div>
    <div class="flex justify-center">
      <div
        class="columns-1 sm:columns-2 md:columns-3 lg:columns-4 gap-4 max-w-7xl space-y-4 mb-8"
      >
        <div
          v-for="artwork in filteredList()"
          :key="artwork._id"
          class="break-after-all break-inside-avoid-column"
        >
          <div
            v-if="artwork.alt_text"
            class="max-w-sm bg-white border border-gray-200 rounded-2xl overflow-hidden shadow dark:bg-gray-800 dark:border-gray-700"
          >
            <img
              class="rounded-t-lg w-full"
              :src="artwork.preferred_file_url"
              :alt="artwork.alt_text"
              :title="artwork.alt_text"
            />
            <div class="p-5">
              <h5 class="mb-0 text-2xl font-bold text-gray-900 dark:text-white">
                {{ artwork.Title }}
              </h5>
              <p class="text-xl font-normal text-gray-700 dark:text-gray-400">
                {{ artwork.artist }}
              </p>
              <p class="font-normal text-gray-700 dark:text-gray-400">
                {{ artwork.date }}
              </p>
              <p class="font-normal text-gray-700 dark:text-gray-400">
                {{ artwork.medium }}
              </p>
              <div class="flex justify-end text-lg mb-2">
                <p class="font-normal text-gray-700 dark:text-gray-400">
                  <span v-if="artwork.Country == 'Argentina'">🇦🇷</span>
                  <span v-if="artwork.Country == 'Bolívia'">🇧🇴</span>
                  <span v-if="artwork.Country == 'Brasil'">🇧🇷</span>
                  <span v-if="artwork.Country == 'Colômbia'">🇨🇴</span>
                  <span v-if="artwork.Country == 'Chile'"> 🇨🇱 </span>
                  <span v-if="artwork.Country == 'Cuba'">🇨🇺</span>
                  {{ artwork.Country }}
                </p>
              </div>
              <a
                :href="artwork.attribution_url"
                target="_blank"
                class="cursor-pointer w-full inline-flex items-center justify-center px-3 py-2 text-sm font-medium text-center ring-1 text-gray-500 ring-gray-500 dark:ring-gray-400 dark:text-gray-400 bg-transparent rounded-lg hover:bg-blue-500 focus:ring-4 focus:outline-none hover:ring-transparent focus:ring-blue-300 dark:bg-transparent dark:hover:bg-blue-700 dark:focus:ring-blue-800 hover:text-white"
              >
                Saiba mais
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { XMarkIcon } from "@heroicons/vue/24/outline";

import { ref } from "vue";
let input = ref("");
const props = defineProps({
  artworks: {
    type: Array,
    required: true,
  },
});
const { artworks } = props;

function filteredList() {
  return artworks.filter(
    (artwork) =>
      (artwork.Title.toLowerCase().includes(input.value.toLowerCase()) ||
        artwork.artist.toLowerCase().includes(input.value.toLowerCase()) ||
        artwork.date
          .toString()
          .toLowerCase()
          .includes(input.value.toLowerCase()) ||
        artwork.Country.toLowerCase().includes(input.value.toLowerCase())) &&
      artwork.alt_text
  );
}

function handleClear() {
  input.value = "";
}
</script>
