<template>
  <div class="space-y-8">
    <!-- 基础轮播 -->
    <section>
      <h3 class="text-lg font-medium mb-4">基础轮播</h3>
      <div class="h-64">
        <Carousel>
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 1
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
          <template #item-2>
            <div
              class="w-full h-full bg-red-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 3
            </div>
          </template>
        </Carousel>
      </div>
    </section>

    <!-- 自动播放 -->
    <section>
      <h3 class="text-lg font-medium mb-4">自动播放</h3>
      <div class="h-64">
        <Carousel :autoplay="true" :interval="3000">
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 1
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
          <template #item-2>
            <div
              class="w-full h-full bg-red-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 3
            </div>
          </template>
        </Carousel>
      </div>
    </section>

    <!-- 不同尺寸 -->
    <section>
      <h3 class="text-lg font-medium mb-4">不同尺寸</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div>
          <p class="mb-2 text-sm text-gray-600">小尺寸 (sm)</p>
          <Carousel size="sm">
            <template #item-0>
              <div
                class="w-full h-full bg-blue-500 flex items-center justify-center text-white"
              >
                幻灯片 1
              </div>
            </template>
            <template #item-1>
              <div
                class="w-full h-full bg-green-500 flex items-center justify-center text-white"
              >
                幻灯片 2
              </div>
            </template>
          </Carousel>
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-600">中尺寸 (md)</p>
          <Carousel size="md">
            <template #item-0>
              <div
                class="w-full h-full bg-blue-500 flex items-center justify-center text-white"
              >
                幻灯片 1
              </div>
            </template>
            <template #item-1>
              <div
                class="w-full h-full bg-green-500 flex items-center justify-center text-white"
              >
                幻灯片 2
              </div>
            </template>
          </Carousel>
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-600">大尺寸 (lg)</p>
          <Carousel size="lg">
            <template #item-0>
              <div
                class="w-full h-full bg-blue-500 flex items-center justify-center text-white"
              >
                幻灯片 1
              </div>
            </template>
            <template #item-1>
              <div
                class="w-full h-full bg-green-500 flex items-center justify-center text-white"
              >
                幻灯片 2
              </div>
            </template>
          </Carousel>
        </div>
      </div>
    </section>

    <!-- 控制选项 -->
    <section>
      <h3 class="text-lg font-medium mb-4">控制选项</h3>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="h-48">
          <p class="mb-2 text-sm text-gray-600">无导航按钮</p>
          <Carousel :navigation="false">
            <template #item-0>
              <div
                class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-xl"
              >
                无导航按钮
              </div>
            </template>
            <template #item-1>
              <div
                class="w-full h-full bg-green-500 flex items-center justify-center text-white text-xl"
              >
                幻灯片 2
              </div>
            </template>
          </Carousel>
        </div>
        <div class="h-48">
          <p class="mb-2 text-sm text-gray-600">无指示器</p>
          <Carousel :indicators="false">
            <template #item-0>
              <div
                class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-xl"
              >
                无指示器
              </div>
            </template>
            <template #item-1>
              <div
                class="w-full h-full bg-green-500 flex items-center justify-center text-white text-xl"
              >
                幻灯片 2
              </div>
            </template>
          </Carousel>
        </div>
      </div>
    </section>

    <!-- 自定义导航图标 -->
    <section>
      <h3 class="text-lg font-medium mb-4">自定义导航图标</h3>
      <div class="h-64">
        <Carousel>
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 1
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
          <template #item-2>
            <div
              class="w-full h-full bg-red-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 3
            </div>
          </template>

          <template #prev-icon>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M15 19l-7-7 7-7"
              />
            </svg>
          </template>

          <template #next-icon>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 5l7 7-7 7"
              />
            </svg>
          </template>
        </Carousel>
      </div>
    </section>

    <!-- 图片轮播 -->
    <section>
      <h3 class="text-lg font-medium mb-4">图片轮播</h3>
      <div class="h-64">
        <Carousel :autoplay="true" :interval="3000">
          <template
            v-for="(image, index) in images"
            :key="index"
            v-slot:[`item-${index}`]
          >
            <div class="w-full h-full">
              <img
                :src="image"
                class="w-full h-full object-cover"
                :alt="`图片 ${index + 1}`"
              />
            </div>
          </template>
        </Carousel>
      </div>
    </section>

    <!-- 程序控制轮播 -->
    <section>
      <h3 class="text-lg font-medium mb-4">程序控制轮播</h3>
      <div class="h-64 mb-4">
        <Carousel ref="carouselRef" :navigation="false">
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 1
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
          <template #item-2>
            <div
              class="w-full h-full bg-red-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 3
            </div>
          </template>
        </Carousel>
      </div>

      <div class="flex gap-2">
        <button
          class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
          @click="prevSlide"
        >
          上一项
        </button>
        <button
          class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
          @click="nextSlide"
        >
          下一项
        </button>
        <div class="flex gap-2 ml-4">
          <button
            v-for="i in 3"
            :key="i"
            class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600"
            @click="goToSlide(i - 1)"
          >
            {{ i }}
          </button>
        </div>
      </div>
    </section>

    <!-- 自定义样式 -->
    <section>
      <h3 class="text-lg font-medium mb-4">自定义样式</h3>
      <div class="h-64">
        <Carousel
          :pt="{
            root: 'rounded-lg shadow-xl overflow-hidden',
            prevButton: 'bg-black/50 text-white',
            nextButton: 'bg-black/50 text-white',
            indicator: 'w-3 h-3 bg-gray-300',
            activeIndicator: 'w-6 h-3 bg-white',
          }"
          :autoplay="true"
        >
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 1
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
          <template #item-2>
            <div
              class="w-full h-full bg-red-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 3
            </div>
          </template>
        </Carousel>
      </div>
    </section>

    <!-- 禁用状态 -->
    <section>
      <h3 class="text-lg font-medium mb-4">禁用状态</h3>
      <div class="h-64">
        <Carousel :disabled="true">
          <template #item-0>
            <div
              class="w-full h-full bg-blue-500 flex items-center justify-center text-white text-2xl"
            >
              已禁用轮播
            </div>
          </template>
          <template #item-1>
            <div
              class="w-full h-full bg-green-500 flex items-center justify-center text-white text-2xl"
            >
              幻灯片 2
            </div>
          </template>
        </Carousel>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Carousel } from '@versakit/vue'

// 图片轮播数据
const images = [
  'https://picsum.photos/id/1018/800/400',
  'https://picsum.photos/id/1015/800/400',
  'https://picsum.photos/id/1019/800/400',
  'https://picsum.photos/id/1016/800/400',
]

// 程序控制轮播
const carouselRef = ref(null)

const nextSlide = () => {
  carouselRef.value?.next()
}

const prevSlide = () => {
  carouselRef.value?.prev()
}

const goToSlide = (index: number) => {
  carouselRef.value?.goToSlide(index)
}
</script>
