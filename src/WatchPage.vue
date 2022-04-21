<script setup lang="ts">
import { Model, OrbitCamera, useAnimation, World } from "lingo3d-vue"
const anim = useAnimation({ from: 180, to: 0, duration: 5000 })
</script>

<template>
  <div class="w-full h-full bg-slate-500 relative">
    <div :style="{ backgroundImage: `url(bg.jpg)` }" class="bg-cover bg-center w-full h-full absolute overflow-hidden text-white">
      <div class="absolute left-0 top-0 w-full h-full bg-gradient-to-t from-gray-700 to-black opacity-75" />
      <div class="relative">
        <div class="text-5xl font-bold text-center" :style="{ transform: `scale(2.5) translateY(50%)` }">Apple<br />Watch<br />Series</div>
      </div>
    </div>
    <div class="absolute bottom-0 w-full p-6">
      <div class="text-center text-lg opacity-50 text-[#e5e7eb]">swipe to rotate</div>
      <div class="text-center text-xs text-white">powered by Lingo3D</div>
    </div>
  </div>
  <World color="transparent" defaultLight="studio">
    <Model src="apple_watch/scene.gltf" :y="-50" :rotationZ="anim" :boxVisible="false" />
    <OrbitCamera active :z="200" :y="80" :zoom="1.5" autoRotate enableDamping />
  </World>
</template>
