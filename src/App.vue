<script setup lang="ts">
import WatchPage from "./WatchPage.vue"
import { ref, watchEffect } from "vue"
import { usePreload } from "lingo3d-vue"

const progress = usePreload(["bg.jpg", "apple_watch/scene.bin", "apple_watch/scene.gltf", "apple_watch/textures/material_baseColor.jpeg"], "573kb")

const displayLoading = ref(true)

watchEffect(() => {
  if (progress.value > 99) {
    displayLoading.value = false
  }
})
</script>

<template>
  <div v-if="displayLoading" class="w-screen h-screen absolute bg-black text-white flex justify-center items-center">loading, please wait</div>
  <WatchPage v-else />
</template>
