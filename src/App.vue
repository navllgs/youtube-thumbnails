<template>
  <div class="p-8 animate-slidein">
    <h1 class="text-center font-bold text-5xl">Youtube Thumbnails</h1>
    <h1 class="text-center font-bold text-2xl mb-8">List of Youtube Thumbnails</h1>
    <div class="d-flex pt-2">
      <CategoryItem @onButtonClicked="isActiveCategory = i" class="pill-button m-1" :isActive="isActiveCategory == i"
        v-for="(catogry, i) in categoryList" :key="i" :title="catogry"></CategoryItem>
    </div>
    <div class="border border-gray-300 my-4"></div>
    <div class="grid max-sm:grid-cols-1 max-md:grid-cols-3 grid-cols-3 gap-4">
      <template v-if="!isLoading">
        <div v-for="youtubeData, i in categorizedData" :key="i" class="aspect-[14/9] animate-slidein">
          <YoutubeThumbnailItem :title="youtubeData.title" :thumbnail="youtubeData.url" />
        </div>
      </template>
      <template v-if="isLoading">
        <div v-for="i in 3" :key="i" class="aspect-[14/9]">
          <YoutubeThumbnailItemLoading />
        </div>
      </template>
    </div>
  </div>
</template>

<script setup lang="ts">
import YoutubeThumbnailItem from './components/YoutubeThumbnailItem.vue'
import CategoryItem from './components/CategoryItem.vue'
import YoutubeThumbnailItemLoading from './components/YoutubeThumbnailItemLoading.vue'
import { ref, computed, watch } from "vue"
import DATA from "./jsons/data.json"
import type { YoutubeObj } from "./interface/YoutubeInterface.ts"

const youtubeThumbnails = ref<YoutubeObj[]>(DATA.youtubeDataThumbnails)
const isActiveCategory = ref(0)
const isLoading = ref(false)
const categoryList = ref(["All", "Arts", "Sports", "Fitness"])

watch(isActiveCategory, () => {
  isLoading.value = true

  setTimeout(() => {
    isLoading.value = false
  }, 1000)
})

const categorizedData = computed(() => {
  if (isActiveCategory.value == 0) return youtubeThumbnails.value;
  if (isActiveCategory.value == 1) return youtubeThumbnails.value.slice(0, 3);

  return youtubeThumbnails.value.filter((data, i) => { return i % isActiveCategory.value })
})

</script>