<template>
  <view class="bg-gray-50 min-h-screen pb-20">
    <!-- Top Actions -->
    <view class="grid grid-cols-3 gap-3 p-4">
      <view class="flex flex-col gap-2 rounded-xl bg-white p-4 items-center justify-center shadow-sm" @click="goToScanDispense">
        <view class="bg-blue-50 p-3 rounded-full text-blue-500 mb-1">
          <div class="i-material-symbols-qr-code-scanner text-3xl"></div>
        </view>
        <text class="text-xs font-bold text-gray-900">扫码打水</text>
      </view>
      <view class="flex flex-col gap-2 rounded-xl bg-white p-4 items-center justify-center shadow-sm" @click="goToScanBuy">
        <view class="bg-blue-50 p-3 rounded-full text-blue-500 mb-1">
          <div class="i-material-symbols-credit-card text-3xl"></div>
        </view>
        <text class="text-xs font-bold text-gray-900">扫码购卡</text>
      </view>
      <view class="flex flex-col gap-2 rounded-xl bg-white p-4 items-center justify-center shadow-sm" @click="goToRecharge">
        <view class="bg-blue-50 p-3 rounded-full text-blue-500 mb-1">
          <div class="i-material-symbols-account-balance-wallet text-3xl"></div>
        </view>
        <text class="text-xs font-bold text-gray-900">水卡充值</text>
      </view>
    </view>

    <!-- Card Section -->
    <view class="px-4">
      <view class="flex justify-between items-end border-b border-gray-200">
        <view class="flex gap-6">
          <view
            class="flex flex-col items-center justify-center pb-3 pt-2 border-b-3 transition-colors"
            :class="activeTab === 0 ? 'border-blue-500 text-blue-500' : 'border-transparent text-gray-400'"
            @click="activeTab = 0"
          >
            <text class="text-sm font-bold tracking-wide">电子水卡</text>
          </view>
          <view
            class="flex flex-col items-center justify-center pb-3 pt-2 border-b-3 transition-colors"
            :class="activeTab === 1 ? 'border-blue-500 text-blue-500' : 'border-transparent text-gray-400'"
            @click="activeTab = 1"
          >
            <text class="text-sm font-bold tracking-wide">实体水卡</text>
          </view>
        </view>
        <view class="flex items-center gap-1 text-blue-500 pb-4" @click="goToBindCard">
          <div class="i-material-symbols-add text-sm"></div>
          <text class="text-xs font-bold">绑定新卡</text>
        </view>
      </view>
    </view>

    <!-- Card Display -->
    <view class="p-4">
      <view v-if="activeTab === 0" class="w-full h-44 rounded-xl relative overflow-hidden bg-gradient-to-br from-blue-500 to-blue-400 p-5 flex flex-col justify-between text-white shadow-lg">
        <div class="absolute top-0 right-0 p-4 opacity-20">
          <div class="i-material-symbols-water-drop text-9xl"></div>
        </div>
        <view class="z-10">
          <text class="text-xs opacity-80 mb-1 block">我的电子水卡</text>
          <text class="text-lg font-bold">1029 4852 9384</text>
        </view>
        <view class="z-10">
          <text class="text-xs opacity-80 block">余额</text>
          <view class="flex items-baseline gap-1">
            <text class="text-sm">¥</text>
            <text class="text-3xl font-bold">58.50</text>
          </view>
        </view>
      </view>

      <view v-if="activeTab === 1" class="w-full h-44 rounded-xl relative overflow-hidden bg-white border border-gray-200 p-5 flex flex-col justify-between text-gray-900 shadow-sm">
        <div class="absolute top-0 right-0 p-4 opacity-10">
           <div class="i-material-symbols-credit-card text-9xl"></div>
        </div>
        <view class="z-10">
          <view class="flex justify-between items-start">
            <view>
              <text class="text-xs opacity-60 mb-1 block">家人共享卡</text>
              <text class="text-lg font-bold">8821 5532 1102</text>
            </view>
            <view class="bg-green-100 text-green-700 text-xs px-2 py-0.5 rounded-full font-bold">已激活</view>
          </view>
        </view>
        <view class="z-10">
          <text class="text-xs opacity-60 block">余额</text>
          <view class="flex items-baseline gap-1">
            <text class="text-sm">¥</text>
            <text class="text-3xl font-bold">120.00</text>
          </view>
        </view>
      </view>
    </view>

    <!-- Records -->
    <view class="px-4 mt-2">
      <view class="flex justify-between items-center pb-4">
        <text class="text-gray-900 text-lg font-bold">本月打水记录</text>
        <text class="text-blue-500 text-sm font-medium">查看更多</text>
      </view>

      <view class="space-y-3">
        <view class="flex items-center gap-4 bg-white p-4 rounded-xl shadow-sm border border-gray-100">
          <view class="w-10 h-10 rounded-full bg-blue-50 flex items-center justify-center text-blue-500">
             <div class="i-material-symbols-water-drop"></div>
          </view>
          <view class="flex-1">
            <view class="flex justify-between">
              <text class="font-bold text-gray-900">智慧社区A栋1号机</text>
              <text class="text-gray-400 text-sm">- ¥2.00</text>
            </view>
            <view class="flex justify-between items-center mt-1">
              <text class="text-gray-500 text-xs">打水量: 5.0L</text>
              <text class="text-gray-400 text-xs">2023-11-24 08:30</text>
            </view>
            <text class="text-gray-400 text-xs mt-0.5 block">剩余余额: ¥56.50</text>
          </view>
        </view>

        <view class="flex items-center gap-4 bg-white p-4 rounded-xl shadow-sm border border-gray-100">
          <view class="w-10 h-10 rounded-full bg-blue-50 flex items-center justify-center text-blue-500">
             <div class="i-material-symbols-water-drop"></div>
          </view>
          <view class="flex-1">
            <view class="flex justify-between">
              <text class="font-bold text-gray-900">智慧社区公园东侧机</text>
              <text class="text-gray-400 text-sm">- ¥3.50</text>
            </view>
            <view class="flex justify-between items-center mt-1">
              <text class="text-gray-500 text-xs">打水量: 8.7L</text>
              <text class="text-gray-400 text-xs">2023-11-22 17:15</text>
            </view>
            <text class="text-gray-400 text-xs mt-0.5 block">剩余余额: ¥58.50</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const activeTab = ref(0)

const goToScanDispense = () => {
  // Directly scan
  uni.scanCode({
    success: (res) => {
        // Mock navigate to dispense with some ID
        uni.navigateTo({ url: '/pages/scan/dispense' })
    },
    fail: () => {
        // Fallback for simulator
        uni.navigateTo({ url: '/pages/scan/dispense' })
    }
  })
}

const goToScanBuy = () => {
   uni.scanCode({
    success: (res) => {
        uni.navigateTo({ url: '/pages/card/buy' })
    },
    fail: () => {
        uni.navigateTo({ url: '/pages/card/buy' })
    }
  })
}

const goToRecharge = () => {
  uni.navigateTo({ url: '/pages/card/recharge' })
}

const goToBindCard = () => {
  uni.navigateTo({ url: '/pages/card/bind' })
}
</script>
