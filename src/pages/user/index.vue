<template>
  <view class="bg-gray-50 min-h-screen pb-20">
    <!-- User Header -->
    <view class="bg-white p-6 mb-3">
      <view class="flex items-center gap-4">
        <view class="w-20 h-20 rounded-full border-2 border-blue-100 bg-gray-200 bg-cover bg-center overflow-hidden">
             <!-- Placeholder Avatar -->
             <div class="i-material-symbols-person text-6xl text-gray-400 w-full h-full flex items-center justify-center"></div>
        </view>
        <view class="flex flex-col">
          <text class="text-xl font-bold text-gray-900">张益达</text>
          <text class="text-gray-500 text-sm mt-1">138 8888 8888</text>
          <view class="mt-2 flex items-center gap-2">
            <view class="px-2 py-0.5 bg-blue-50 text-blue-500 text-xs font-bold rounded-full border border-blue-100 uppercase">黄金会员</view>
          </view>
        </view>
      </view>
    </view>

    <!-- Balance Card -->
    <view class="px-4 mb-6">
      <view class="bg-blue-500 rounded-xl p-4 text-white flex justify-between items-center shadow-lg shadow-blue-500/20">
        <view>
          <text class="text-blue-100 text-xs mb-1 block">账户余额 (元)</text>
          <text class="text-2xl font-bold">¥ 128.50</text>
        </view>
        <button class="bg-white text-blue-500 px-4 py-2 rounded-lg font-bold text-sm border-none">立即充值</button>
      </view>
    </view>

    <!-- Grid Actions -->
    <view class="grid grid-cols-3 gap-4 px-4 mb-6">
      <view class="flex flex-col items-center justify-center p-4 bg-white rounded-xl border border-gray-100 shadow-sm active:scale-95 transition-transform" @click="goToRecords('recharge')">
        <view class="w-12 h-12 rounded-full bg-blue-50 flex items-center justify-center text-blue-600 mb-2">
          <div class="i-material-symbols-receipt-long text-2xl"></div>
        </view>
        <text class="text-sm font-medium">充值记录</text>
      </view>
      <view class="flex flex-col items-center justify-center p-4 bg-white rounded-xl border border-gray-100 shadow-sm active:scale-95 transition-transform" @click="goToRecords('dispense')">
        <view class="w-12 h-12 rounded-full bg-cyan-50 flex items-center justify-center text-cyan-600 mb-2">
          <div class="i-material-symbols-water-drop text-2xl"></div>
        </view>
        <text class="text-sm font-medium">打水记录</text>
      </view>
      <view class="flex flex-col items-center justify-center p-4 bg-white rounded-xl border border-gray-100 shadow-sm active:scale-95 transition-transform" @click="goToRecords('buy')">
        <view class="w-12 h-12 rounded-full bg-indigo-50 flex items-center justify-center text-indigo-600 mb-2">
           <div class="i-material-symbols-credit-card text-2xl"></div>
        </view>
        <text class="text-sm font-medium">购卡记录</text>
      </view>
    </view>

    <!-- Menu List -->
    <view class="mx-4 bg-white rounded-xl overflow-hidden border border-gray-100 mb-6">
      <view class="flex items-center gap-4 px-4 py-4 border-b border-gray-50 active:bg-gray-50" @click="goToCardWallet">
        <view class="flex items-center justify-center text-blue-500">
          <div class="i-material-symbols-style text-xl"></div>
        </view>
        <text class="flex-1 text-base font-medium">我的实体卡</text>
        <view class="text-gray-400 flex items-center">
          <text class="text-xs mr-1 text-gray-500">2张可用</text>
          <div class="i-material-symbols-chevron-right text-xl"></div>
        </view>
      </view>
      <view class="flex items-center gap-4 px-4 py-4 border-b border-gray-50 active:bg-gray-50" @click="goToCardWallet">
        <view class="flex items-center justify-center text-blue-500">
           <div class="i-material-symbols-smart-button text-xl"></div>
        </view>
        <text class="flex-1 text-base font-medium">我的电子卡</text>
        <view class="text-gray-400 flex items-center">
          <div class="i-material-symbols-chevron-right text-xl"></div>
        </view>
      </view>
      <view class="flex items-center gap-4 px-4 py-4 border-b border-gray-50 active:bg-gray-50" @click="goToLocations">
        <view class="flex items-center justify-center text-blue-500">
           <div class="i-material-symbols-location-on text-xl"></div>
        </view>
        <text class="flex-1 text-base font-medium">常用饮水点</text>
        <view class="text-gray-400 flex items-center">
          <div class="i-material-symbols-chevron-right text-xl"></div>
        </view>
      </view>
      <view class="flex items-center gap-4 px-4 py-4 border-b border-gray-50 active:bg-gray-50" @click="callService">
        <view class="flex items-center justify-center text-blue-500">
           <div class="i-material-symbols-support-agent text-xl"></div>
        </view>
        <text class="flex-1 text-base font-medium">客服电话</text>
        <view class="text-gray-400 flex items-center">
          <text class="text-xs mr-1 text-gray-500">400-888-9999</text>
           <div class="i-material-symbols-call text-xl"></div>
        </view>
      </view>
    </view>

    <!-- Banner -->
    <view class="px-4 mb-6">
      <view class="relative h-24 rounded-xl overflow-hidden bg-gradient-to-r from-blue-600 to-blue-400 flex items-center p-4">
        <view class="z-10">
          <text class="text-white font-bold block">健康饮水知识</text>
          <text class="text-blue-100 text-xs mt-1 block">每天八杯水，健康常相随</text>
        </view>
        <view class="absolute right-0 bottom-0 opacity-20 transform translate-y-4">
           <div class="i-material-symbols-water text-9xl text-white"></div>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
const goToRecords = (type: string) => {
  uni.showToast({ title: `查看${type}记录`, icon: 'none' })
}

const goToCardWallet = () => {
  uni.navigateTo({ url: '/pages/card/wallet' })
}

const goToLocations = () => {
  uni.navigateTo({ url: '/pages/location/index' })
}

const callService = () => {
  uni.makePhoneCall({ phoneNumber: '4008889999' })
}
</script>
