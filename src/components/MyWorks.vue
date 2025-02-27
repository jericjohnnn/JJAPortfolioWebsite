<template>
  <div
    :class="[' text-white transition-colors duration-500', isOnDevView ? 'bg-black' : 'bg-yellow']"
  >
    <div class="container mx-auto lg:h-screen px-4 py-14 flex flex-col justify-between">
      <div class="flex flex-col items-center mb-8">
        <h2
          :class="[
            'text-4xl md:text-5xl font-bold text-center transition-colors duration-300',
            isOnDevView ? 'text-yellow' : 'text-black',
          ]"
        >
          MY WORKS
        </h2>
        <div
          :class="[
            'flex items-center mt-2 p-1 rounded-full bottom-8 right-4 transition-colors duration-500 group',
            isOnDevView ? 'bg-yellow' : 'bg-black',
          ]"
        >
          <button
            @click="toggleisOnDevView"
            :class="[
              'flex items-center gap-1 p-1 rounded-full transition-all duration-500 ease-in-out w-16 justify-center',
              isOnDevView ? 'bg-black' : '',
            ]"
          >
            <CodeXml size="16" color="#F6E332" />
            <p class="text-sm text-yellow">Dev</p>
          </button>
          <button
            @click="toggleisOnDevView"
            :class="[
              'flex items-center gap-1 p-1 rounded-full transition-all duration-500 ease-in-out w-16 justify-center',
              !isOnDevView ? 'bg-yellow' : '',
            ]"
          >
            <Palette :size="16" color="#0E161E" />
            <p class="text-sm text-black">Gfx</p>
          </button>
        </div>
      </div>
      <div class="flex justify-center items-center py-5">
        <MyWorksWeb v-show="isOnDevView" />
        <MyWorksGfx v-show="!isOnDevView" />
      </div>
      <div></div>
    </div>
  </div>
</template>

<script setup>
import MyWorksGfx from './MyWorksGfx.vue'
import MyWorksWeb from './MyWorksWeb.vue'
import { CodeXml, Palette } from 'lucide-vue-next'
import { debounce } from 'lodash'
import { ref } from 'vue'

const isOnDevView = ref(true)

const toggleisOnDevView = debounce(() => {
  isOnDevView.value = !isOnDevView.value
}, 200)
</script>
