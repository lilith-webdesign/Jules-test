<template>
  <view class="bg-gray-50 min-h-screen pb-24 flex flex-col">
    <!-- Header Info -->
    <view class="px-4 pt-4 pb-2">
      <text class="text-gray-900 text-2xl font-bold block">设备编号: 8902-A</text>
      <view class="flex items-start gap-2 mt-2">
        <div class="i-material-symbols-location-on text-gray-500 text-lg mt-0.5"></div>
        <text class="text-gray-500 text-sm">位置: 阳光小区3号楼西侧单元门口</text>
      </view>
    </view>

    <!-- Status Cards -->
    <view class="flex flex-wrap gap-4 p-4">
      <view class="flex min-w-[150px] flex-1 flex-col gap-2 rounded-xl p-5 bg-white border border-gray-200 shadow-sm">
        <view class="flex items-center gap-2 mb-1">
          <div class="i-material-symbols-water-drop text-blue-500 text-xl"></div>
          <text class="text-gray-500 text-sm font-medium">设备剩余水量</text>
        </view>
        <text class="text-gray-900 text-2xl font-bold">充足</text>
      </view>
      <view class="flex min-w-[150px] flex-1 flex-col gap-2 rounded-xl p-5 bg-white border border-gray-200 shadow-sm">
        <view class="flex items-center gap-2 mb-1">
          <div class="i-material-symbols-account-balance-wallet text-green-500 text-xl"></div>
          <text class="text-gray-500 text-sm font-medium">当前卡内余额</text>
        </view>
        <text class="text-gray-900 text-2xl font-bold">¥ 45.50</text>
      </view>
    </view>

    <!-- Selection -->
    <view class="px-4 py-2">
      <text class="text-gray-900 text-lg font-bold mb-4 block">选择水量</text>
      <view class="grid grid-cols-2 gap-4">
        <view
          v-for="(opt, idx) in options"
          :key="idx"
          class="relative flex flex-col items-center justify-center gap-3 rounded-xl p-6 border-2 transition-all"
          :class="selected === idx ? 'border-blue-500 bg-blue-50' : 'border-transparent bg-white shadow-sm'"
          @click="selected = idx"
        >
          <div v-if="selected === idx" class="absolute top-3 right-3 text-blue-500">
             <div class="i-material-symbols-check-circle text-xl"></div>
          </div>
          <view
            class="w-12 h-12 rounded-full flex items-center justify-center transition-colors"
            :class="selected === idx ? 'bg-blue-100' : 'bg-gray-100'"
          >
             <div :class="[opt.icon, selected === idx ? 'text-blue-500' : 'text-gray-500']" class="text-2xl"></div>
          </view>
          <view class="text-center">
            <text class="block text-gray-900 text-lg font-bold" :class="{'text-blue-500': selected === idx}">{{ opt.label }}</text>
            <text class="block text-gray-500 text-xs" :class="{'text-blue-400': selected === idx}">{{ opt.sub }}</text>
          </view>
        </view>
      </view>
    </view>

    <!-- Bottom Bar -->
    <view class="fixed bottom-0 left-0 right-0 p-4 bg-white border-t border-gray-200 shadow-lg">
      <view class="flex items-center justify-between mb-3 px-1">
        <view class="flex flex-col">
          <text class="text-xs text-gray-500">预计支付</text>
          <text class="text-xl font-bold text-gray-900">¥ {{ options[selected].price }}</text>
        </view>
        <view class="text-xs text-blue-500 bg-blue-50 px-2 py-1 rounded">优惠已抵扣 ¥0.00</view>
      </view>
      <button class="w-full flex items-center justify-center gap-2 rounded-xl bg-blue-500 px-5 py-4 text-white shadow-md active:scale-95 border-none" @click="startDispense">
        <div class="i-material-symbols-water-drop text-2xl"></div>
        <text class="text-base font-bold tracking-wide">开始打水</text>
      </button>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const selected = ref(1)

const options = [
  { label: '500ml', sub: '¥ 0.50', price: '0.50', icon: 'i-material-symbols-local-drink' },
  { label: '1.5L', sub: '¥ 1.20', price: '1.20', icon: 'i-material-symbols-water-bottle' },
  { label: '5L', sub: '¥ 3.50', price: '3.50', icon: 'i-material-symbols-water-full' },
  { label: '自定义', sub: '按量计费', price: '0.00', icon: 'i-material-symbols-settings' },
]

const startDispense = () => {
  uni.showLoading({ title: '启动中...' })
  setTimeout(() => {
    uni.hideLoading()
    uni.showToast({ title: '出水中...', icon: 'success' })
  }, 1000)
}
</script>
