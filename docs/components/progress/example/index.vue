<template>
  <div class="space-y-8">
    <!-- 基础进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">基础进度条</h3>
      <Progress :value="40" />
    </section>

    <!-- 带文本的进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">带文本的进度条</h3>
      <Progress :value="60" showText />
    </section>

    <!-- 不同大小的进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">不同大小的进度条</h3>
      <div class="space-y-4">
        <div>
          <p class="mb-2 text-sm text-gray-500">小号进度条</p>
          <Progress :value="30" size="sm" />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">中号进度条</p>
          <Progress :value="50" size="md" />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">大号进度条</p>
          <Progress :value="70" size="lg" />
        </div>
      </div>
    </section>

    <!-- 不同形状的进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">不同形状的进度条</h3>
      <div class="space-y-4">
        <div>
          <p class="mb-2 text-sm text-gray-500">方形进度条</p>
          <Progress :value="40" shape="flat" />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">圆角进度条</p>
          <Progress :value="60" shape="rounded" />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">胶囊形进度条</p>
          <Progress :value="80" shape="pill" />
        </div>
      </div>
    </section>

    <!-- 不同状态的进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">不同状态的进度条</h3>
      <div class="space-y-4">
        <div>
          <p class="mb-2 text-sm text-gray-500">默认状态</p>
          <Progress :value="40" variant="default" showText />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">成功状态</p>
          <Progress :value="100" variant="success" showText />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">警告状态</p>
          <Progress :value="70" variant="warning" showText />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">危险状态</p>
          <Progress :value="20" variant="danger" showText />
        </div>
        <div>
          <p class="mb-2 text-sm text-gray-500">信息状态</p>
          <Progress :value="50" variant="info" showText />
        </div>
      </div>
    </section>

    <!-- 条纹进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">条纹进度条</h3>
      <Progress :value="60" striped />
    </section>

    <!-- 动画进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">动画进度条</h3>
      <Progress :value="60" striped animated />
    </section>

    <!-- 不确定状态进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">不确定状态进度条</h3>
      <Progress indeterminate />
    </section>

    <!-- 自定义文本 -->
    <section>
      <h3 class="text-lg font-medium mb-4">自定义文本</h3>
      <Progress :value="75" showText>
        <template #text>
          <span class="font-bold">{{ Math.round(75) }}分 / 100分</span>
        </template>
      </Progress>
    </section>

    <!-- 动态进度条 -->
    <section>
      <h3 class="text-lg font-medium mb-4">动态进度条</h3>
      <div class="space-y-4">
        <Progress :value="dynamicValue" showText />
        <div class="flex items-center gap-4">
          <button
            @click="startProgress"
            class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
            :disabled="isProgressing"
          >
            开始进度
          </button>
          <button
            @click="resetProgress"
            class="px-4 py-2 bg-gray-200 rounded hover:bg-gray-300"
          >
            重置
          </button>
        </div>
      </div>
    </section>

    <!-- 无样式模式 -->
    <section>
      <h3 class="text-lg font-medium mb-4">无样式模式</h3>
      <Progress
        :value="50"
        unstyled
        :pt="{
          root: 'w-full',
          container: 'w-full h-4 bg-gray-100 rounded-full overflow-hidden',
          bar: 'h-full bg-gradient-to-r from-purple-500 to-pink-500',
          text: 'text-right text-sm font-medium text-purple-700 mt-1',
        }"
        showText
      />
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Progress } from '@versakit/vue'

const dynamicValue = ref(0)
const isProgressing = ref(false)

const startProgress = () => {
  if (isProgressing.value) return

  isProgressing.value = true
  dynamicValue.value = 0

  const interval = setInterval(() => {
    dynamicValue.value += 1

    if (dynamicValue.value >= 100) {
      clearInterval(interval)
      isProgressing.value = false
    }
  }, 50)
}

const resetProgress = () => {
  dynamicValue.value = 0
}
</script>
