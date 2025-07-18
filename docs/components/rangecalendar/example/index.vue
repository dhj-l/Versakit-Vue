<script setup lang="ts">
import { RangeCalendar } from '@versakit/vue'
import '@versakit/vue/style'
import { ref } from 'vue'

const basicRange = ref<[Date | null, Date | null]>([null, null])
const defaultRange = ref<[Date | null, Date | null]>([
  new Date(2023, 0, 15),
  new Date(2023, 0, 20),
])
const limitedRange = ref<[Date | null, Date | null]>([null, null])
const disabledRange = ref<[Date | null, Date | null]>([
  new Date(2023, 0, 15),
  new Date(2023, 0, 20),
])
const readonlyRange = ref<[Date | null, Date | null]>([
  new Date(2023, 0, 15),
  new Date(2023, 0, 20),
])
const mondayFirstRange = ref<[Date | null, Date | null]>([null, null])
const localeRange = ref<[Date | null, Date | null]>([null, null])
const customStyleRange = ref<[Date | null, Date | null]>([null, null])
const unstyledRange = ref<[Date | null, Date | null]>([null, null])

// 检测当前主题模式
const isDarkMode = ref(false)

// 监听系统主题变化
if (typeof window !== 'undefined') {
  // 初始化主题
  isDarkMode.value =
    document.documentElement.classList.contains('dark') ||
    window.matchMedia('(prefers-color-scheme: dark)').matches

  // 监听主题变化
  window
    .matchMedia('(prefers-color-scheme: dark)')
    .addEventListener('change', (e) => {
      isDarkMode.value = e.matches
    })
}

// 格式化日期范围显示
const formatDateRange = (range: [Date | null, Date | null]): string => {
  if (!range[0] || !range[1]) return '未选择'

  const formatDate = (date: Date): string => {
    return `${date.getFullYear()}-${String(date.getMonth() + 1).padStart(2, '0')}-${String(date.getDate()).padStart(2, '0')}`
  }

  return `${formatDate(range[0])} 至 ${formatDate(range[1])}`
}
</script>

<template>
  <div class="space-y-12">
    <!-- 基础用法 -->
    <section class="example-section">
      <h2 class="example-title">基础用法</h2>
      <div class="example-container">
        <RangeCalendar v-model="basicRange" />
        <div class="selection-info">
          已选择: {{ formatDateRange(basicRange) }}
        </div>
      </div>
    </section>

    <!-- 默认选中日期 -->
    <section class="example-section">
      <h2 class="example-title">默认选中日期</h2>
      <div class="example-container">
        <RangeCalendar v-model="defaultRange" />
        <div class="selection-info">
          已选择: {{ formatDateRange(defaultRange) }}
        </div>
      </div>
    </section>

    <!-- 日期范围限制 -->
    <section class="example-section">
      <h2 class="example-title">日期范围限制</h2>
      <div class="example-container">
        <RangeCalendar
          v-model="limitedRange"
          :min-date="new Date(2023, 0, 1)"
          :max-date="new Date(2023, 11, 31)"
        />
        <div class="selection-info">
          已选择: {{ formatDateRange(limitedRange) }}
          <div class="selection-constraint">
            (可选范围: 2023-01-01 至 2023-12-31)
          </div>
        </div>
      </div>
    </section>

    <!-- 禁用状态 -->
    <section class="example-section">
      <h2 class="example-title">禁用状态</h2>
      <div class="example-container">
        <RangeCalendar v-model="disabledRange" disabled />
        <div class="selection-info">
          已选择: {{ formatDateRange(disabledRange) }}
        </div>
      </div>
    </section>

    <!-- 只读状态 -->
    <section class="example-section">
      <h2 class="example-title">只读状态</h2>
      <div class="example-container">
        <RangeCalendar v-model="readonlyRange" readonly />
        <div class="selection-info">
          已选择: {{ formatDateRange(readonlyRange) }}
        </div>
      </div>
    </section>

    <!-- 周一作为一周的第一天 -->
    <section class="example-section">
      <h2 class="example-title">周一作为一周的第一天</h2>
      <div class="example-container">
        <RangeCalendar v-model="mondayFirstRange" :first-day-of-week="1" />
        <div class="selection-info">
          已选择: {{ formatDateRange(mondayFirstRange) }}
        </div>
      </div>
    </section>

    <!-- 本地化设置 -->
    <section class="example-section">
      <h2 class="example-title">本地化设置</h2>
      <div class="example-container">
        <RangeCalendar v-model="localeRange" locale="zh-CN" />
        <div class="selection-info">
          已选择: {{ formatDateRange(localeRange) }}
        </div>
      </div>
    </section>

    <!-- 自定义样式 -->
    <section class="example-section">
      <h2 class="example-title">自定义样式</h2>
      <div class="example-container">
        <RangeCalendar
          v-model="customStyleRange"
          :pt="{
            root: 'border border-gray-300 dark:border-gray-600 rounded-md overflow-hidden',
            header: isDarkMode ? 'bg-blue-900' : 'bg-blue-50',
            title: isDarkMode
              ? 'text-blue-300 font-bold'
              : 'text-blue-700 font-bold',
            weekDay: isDarkMode ? 'text-blue-400' : 'text-blue-500',
            day: {
              selected: isDarkMode
                ? 'bg-blue-600 text-white hover:bg-blue-700'
                : 'bg-blue-500 text-white hover:bg-blue-600',
              inRange: isDarkMode ? 'bg-blue-900' : 'bg-blue-100',
              today: isDarkMode ? 'border-blue-400' : 'border-blue-500',
            },
          }"
        />
        <div class="selection-info">
          已选择: {{ formatDateRange(customStyleRange) }}
        </div>
      </div>
    </section>

    <!-- 无样式模式 -->
    <section class="example-section">
      <h2 class="example-title">无样式模式</h2>
      <div class="example-container">
        <RangeCalendar
          v-model="unstyledRange"
          unstyled
          :pt="{
            root: isDarkMode
              ? 'border border-gray-600 rounded-lg p-4'
              : 'border border-gray-200 rounded-lg p-4',
            header: 'flex justify-between items-center mb-4',
            title: isDarkMode
              ? 'text-lg font-medium text-gray-200'
              : 'text-lg font-medium text-gray-800',
            monthNavPrev: isDarkMode
              ? 'p-1 rounded-full hover:bg-gray-700'
              : 'p-1 rounded-full hover:bg-gray-100',
            monthNavNext: isDarkMode
              ? 'p-1 rounded-full hover:bg-gray-700'
              : 'p-1 rounded-full hover:bg-gray-100',
            weekDays: 'grid grid-cols-7 mb-2',
            weekDay: isDarkMode
              ? 'text-center text-sm font-medium text-gray-400'
              : 'text-center text-sm font-medium text-gray-500',
            days: 'grid grid-cols-7 gap-1',
            day: {
              root: 'flex items-center justify-center h-8 w-8 rounded-full',
              today: isDarkMode
                ? 'border border-blue-400'
                : 'border border-blue-500',
              selected: isDarkMode
                ? 'bg-blue-600 text-white'
                : 'bg-blue-500 text-white',
              inRange: isDarkMode ? 'bg-blue-900' : 'bg-blue-100',
              disabled: isDarkMode
                ? 'text-gray-600 cursor-not-allowed'
                : 'text-gray-300 cursor-not-allowed',
              adjacent: isDarkMode ? 'text-gray-600' : 'text-gray-400',
            },
          }"
        />
        <div class="selection-info">
          已选择: {{ formatDateRange(unstyledRange) }}
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.example-section {
  border-bottom: 1px solid #e5e7eb;
  padding-bottom: 2rem;
}

.dark .example-section {
  border-bottom: 1px solid #374151;
}

.example-title {
  font-size: 1.125rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: #111827;
}

.dark .example-title {
  color: #f9fafb;
}

.example-container {
  padding: 1.5rem;
  background-color: #fff;
  border-radius: 0.5rem;
  border: 1px solid #e5e7eb;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
}

.dark .example-container {
  background-color: #1f2937;
  border-color: #374151;
}

.selection-info {
  margin-top: 1rem;
  font-size: 0.875rem;
  color: #6b7280;
  font-weight: 500;
}

.dark .selection-info {
  color: #9ca3af;
}

.selection-constraint {
  margin-top: 0.25rem;
  font-size: 0.75rem;
  color: #6b7280;
  font-weight: 400;
}

.dark .selection-constraint {
  color: #9ca3af;
}

/* 日历组件暗黑模式适配 */
.v-calendar {
  color: #1f2937;
}

.dark .v-calendar {
  background-color: #1f2937;
  color: #e5e7eb;
}

.v-calendar-header {
  background-color: #f3f4f6;
}

.dark .v-calendar-header {
  background-color: #374151;
}

.v-calendar-weekday {
  color: #4b5563;
}

.dark .v-calendar-weekday {
  color: #9ca3af;
}

.v-calendar-day {
  color: #374151;
}

.dark .v-calendar-day {
  color: #d1d5db;
}

.v-calendar-day.v-calendar-day--adjacent {
  color: #d1d5db;
}

.dark .v-calendar-day.v-calendar-day--adjacent {
  color: #4b5563;
}

.v-calendar-day.v-calendar-day--today {
  border-color: #3b82f6;
}

.dark .v-calendar-day.v-calendar-day--today {
  border-color: #60a5fa;
}

.v-calendar-day.v-calendar-day--selected {
  background-color: #2563eb;
  color: #fff;
}

.dark .v-calendar-day.v-calendar-day--selected {
  background-color: #2563eb;
  color: #fff;
}

.v-calendar-day.v-calendar-day--in-range {
  background-color: #eff6ff;
}

.dark .v-calendar-day.v-calendar-day--in-range {
  background-color: #1e3a8a;
}

/* 响应式布局调整 */
@media (max-width: 768px) {
  .example-container {
    padding: 1rem;
  }
}
</style>
