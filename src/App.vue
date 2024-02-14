<template>
  <div class="h-[500px] w-full p-4">
    <img class=" h-[100%] m-auto" :src="currentImage" />
    <input class="w-full mt-3" type="range" min="0" :max="images.length - 1" v-model="currentIndex" />
  </div>
</template>


<script setup>
import { ref, computed } from 'vue';

// 动态生成图片路径数组
const images = ref([]);
for (let i = 1; i <= 41; i++) {
  const imagePath = new URL(`./assets/images/${i}.webp`, import.meta.url).href;
  images.value.push(imagePath);
}

const currentIndex = ref(0);
const currentImage = computed(() => images.value[currentIndex.value]);
</script>
