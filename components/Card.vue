<template>
  <div
    class="columns-1 sm:columns-2 md:columns-3 lg:columns-4 gap-4 space-y-4 p-4"
  >
    <div v-for="artwork in artworks" class="break-inside-avoid-column">
      <div
        :artwork="artwork"
        :key="artwork._id"
        class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
      >
        <a href="#">
          <img
            class="rounded-t-lg"
            :src="artwork.preferred_file_url"
            :alt="artwork.alt_text"
            :title="artwork.alt_text"
          />
        </a>
        <div class="p-5">
          <h5
            class="mb-0 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
          >
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
          <a :href="artwork.attribution_url">saiba mais</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  artworks: {
    type: Object,
    required: true,
  },
});
const { artworks } = props;
</script>
