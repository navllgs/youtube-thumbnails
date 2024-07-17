<template>
  <div
    class="group h-full w-100 overflow-hidden hover:shadow-lg hover:shadow-gray-400 rounded-lg duration-300 shadow-none transition-shadow">
    <div class="h-full w-100 rounded-lg duration-300 hover:scale-110 cursor-pointer bg-cover relative"
      :style="{ backgroundImage: `url(${props.thumbnail})` }">
      <div class="group-hover:visible invisible bg-black/50 w-full h-full absolute top-0 bottom-0 right-0 left-0">
        <div class="flex flex-col justify-center items-center h-full w-100">
          <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="80" height="80" viewBox="0 0 48 48">
            <path fill="#FF3D00"
              d="M43.2,33.9c-0.4,2.1-2.1,3.7-4.2,4c-3.3,0.5-8.8,1.1-15,1.1c-6.1,0-11.6-0.6-15-1.1c-2.1-0.3-3.8-1.9-4.2-4C4.4,31.6,4,28.2,4,24c0-4.2,0.4-7.6,0.8-9.9c0.4-2.1,2.1-3.7,4.2-4C12.3,9.6,17.8,9,24,9c6.2,0,11.6,0.6,15,1.1c2.1,0.3,3.8,1.9,4.2,4c0.4,2.3,0.9,5.7,0.9,9.9C44,28.2,43.6,31.6,43.2,33.9z">
            </path>
            <path fill="#FFF" d="M20 31L20 17 32 24z"></path>
          </svg>
          <div class="text-white rounded-full px-4 py-1">
            {{ props.title }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  title: String,
  thumbnail: String,
})
</script>