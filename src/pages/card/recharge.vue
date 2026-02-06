<template>
  <view class="bg-gray-50 min-h-screen flex flex-col pb-24">
    <!-- Header -->
    <view class="px-4 py-4">
       <!-- Card Selection -->
       <view class="bg-white rounded-xl p-1 shadow-sm border border-gray-100">
           <view class="grid grid-cols-2 gap-1 bg-gray-100 p-1 rounded-lg">
               <view
                 class="flex items-center justify-center py-2 rounded-md text-sm font-medium transition-all"
                 :class="cardType === 'electronic' ? 'bg-white text-blue-500 shadow-sm' : 'text-gray-500'"
                 @click="cardType = 'electronic'"
               >
                   <div class="i-material-symbols-contactless text-lg mr-1.5"></div>
                   <text>电子水卡</text>
               </view>
               <view
                 class="flex items-center justify-center py-2 rounded-md text-sm font-medium transition-all"
                 :class="cardType === 'physical' ? 'bg-white text-blue-500 shadow-sm' : 'text-gray-500'"
                 @click="cardType = 'physical'"
               >
                   <div class="i-material-symbols-credit-card text-lg mr-1.5"></div>
                   <text>实体水卡</text>
               </view>
           </view>

           <!-- Balance -->
           <view class="mt-6 mb-8 text-center flex flex-col items-center">
               <view class="text-sm font-medium text-gray-500 mb-2 flex items-center gap-1">
                   <text>当前余额</text>
                   <div class="i-material-symbols-info text-gray-400"></div>
               </view>
               <view class="relative">
                   <text class="text-3xl font-bold tracking-tight text-gray-900">¥</text>
                   <text class="text-5xl font-extrabold tracking-tighter text-gray-900">24.50</text>
               </view>
               <view class="mt-2 inline-flex items-center rounded-full bg-green-50 px-2.5 py-0.5 text-xs font-medium text-green-700">
                   <text>卡号: 8802 **** 1024</text>
               </view>
           </view>
       </view>
    </view>

    <!-- Recharge Amount -->
    <view class="px-4">
        <text class="mb-4 text-base font-bold text-gray-900 block">充值金额</text>
        <view class="grid grid-cols-3 gap-3">
            <view
              v-for="amt in amounts"
              :key="amt.value"
              class="relative flex flex-col items-center justify-center rounded-xl border-2 py-4 shadow-sm transition-all"
              :class="selectedAmount === amt.value ? 'border-blue-500 bg-blue-50' : 'border-transparent bg-white'"
              @click="selectedAmount = amt.value"
            >
                <text class="text-xl font-bold" :class="selectedAmount === amt.value ? 'text-blue-500' : 'text-gray-900'">{{ amt.label }}</text>
                <text v-if="amt.value !== 'custom'" class="text-xs text-gray-400 mt-1 line-through">¥{{ amt.value }}.00</text>

                <view v-if="selectedAmount === amt.value" class="absolute -top-2 -right-2 w-5 h-5 rounded-full bg-blue-500 flex items-center justify-center text-white shadow-sm">
                    <div class="i-material-symbols-check text-xs"></div>
                </view>

                <view v-if="amt.rec" class="absolute top-0 left-0 w-full h-1 bg-blue-500 rounded-t-xl"></view>
                <text v-if="amt.rec" class="text-xs text-blue-500 mt-1 font-medium absolute bottom-1">推荐</text>
            </view>
        </view>
    </view>

    <!-- Tips -->
    <view class="px-4 mt-4">
        <view class="rounded-lg bg-blue-50 p-4 border border-blue-100 flex gap-3">
            <div class="i-material-symbols-tips-and-updates text-blue-500 shrink-0"></div>
            <view class="text-sm text-gray-600">
                <text class="font-medium text-gray-900 mb-1 block">温馨提示</text>
                <text class="leading-relaxed text-xs block">充值后请将卡片贴近设备感应区，或在下次使用时自动同步余额。</text>
            </view>
        </view>
    </view>

    <!-- Bottom Bar -->
    <view class="fixed bottom-0 left-0 right-0 bg-white p-4 pb-8 shadow-lg border-t border-gray-100">
        <view class="flex items-center justify-between mb-3 px-1">
            <text class="text-sm text-gray-500">实付金额:</text>
            <text class="text-xl font-bold text-blue-500">¥{{ selectedAmount === 'custom' ? '0.00' : selectedAmount + '.00' }}</text>
        </view>
        <button class="w-full rounded-xl bg-blue-500 py-3.5 text-center text-base font-bold text-white shadow-lg active:scale-95 hover:bg-blue-600 border-none flex items-center justify-center" @click="handleRecharge">
            <text>立即充值</text>
        </button>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const cardType = ref('electronic')
const selectedAmount = ref(50)

const amounts = [
    { label: '10元', value: 10 },
    { label: '20元', value: 20 },
    { label: '50元', value: 50, rec: true },
    { label: '100元', value: 100 },
    { label: '200元', value: 200 },
    { label: '其他金额', value: 'custom' },
]

const handleRecharge = () => {
    uni.showLoading({ title: '支付中...' })
    setTimeout(() => {
        uni.hideLoading()
        uni.showToast({ title: '充值成功', icon: 'success' })
        setTimeout(() => {
            uni.navigateBack()
        }, 1500)
    }, 1000)
}
</script>
