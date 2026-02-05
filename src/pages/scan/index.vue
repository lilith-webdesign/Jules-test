<template>
  <view class="bg-black relative w-full h-screen overflow-hidden flex flex-col">
    <!-- Camera Simulator (Image or Camera component) -->
    <!-- In real UniApp, use <camera> or API. Here simulation layout -->
    <view class="absolute inset-0 z-0">
        <!-- Overlay dark -->
        <view class="w-full h-full bg-black opacity-50"></view>
    </view>

    <!-- UI Overlay -->
    <view class="absolute inset-0 z-10 flex flex-col h-full w-full">
      <!-- Header -->
      <view class="flex items-center justify-between p-4 pt-12 pb-2">
        <view class="flex items-center justify-center w-10 h-10 rounded-full bg-white/10 backdrop-blur-sm text-white" @click="goBack">
           <div class="i-material-symbols-arrow-back-ios-new text-2xl"></div>
        </view>
        <text class="text-white text-lg font-bold">扫码识别中</text>
        <view class="flex items-center justify-center w-10 h-10 rounded-full bg-white/10 backdrop-blur-sm text-white">
           <div class="i-material-symbols-flashlight-on text-2xl"></div>
        </view>
      </view>

      <!-- Scanner Area -->
      <view class="flex-1 flex flex-col items-center justify-center relative w-full">
         <view class="relative w-64 h-64 rounded-2xl border-2 border-transparent">
             <!-- Corners -->
             <view class="absolute top-0 left-0 w-8 h-8 border-t-4 border-l-4 border-blue-500 rounded-tl-lg"></view>
             <view class="absolute top-0 right-0 w-8 h-8 border-t-4 border-r-4 border-blue-500 rounded-tr-lg"></view>
             <view class="absolute bottom-0 left-0 w-8 h-8 border-b-4 border-l-4 border-blue-500 rounded-bl-lg"></view>
             <view class="absolute bottom-0 right-0 w-8 h-8 border-b-4 border-r-4 border-blue-500 rounded-br-lg"></view>
             <!-- Scan Line -->
             <view class="absolute top-1/2 left-2 right-2 h-0.5 bg-blue-500 shadow-[0_0_15px_2px_rgba(19,127,236,0.6)] animate-pulse"></view>

             <view class="absolute inset-0 flex items-center justify-center opacity-30">
                 <div class="i-material-symbols-qr-code-scanner text-6xl text-white"></div>
             </view>
         </view>
         <text class="mt-8 text-white/90 text-sm font-medium bg-black/30 px-4 py-2 rounded-full backdrop-blur-sm">对准二维码即可自动扫描</text>

         <!-- Simulation Button for Demo -->
         <button class="mt-8 bg-blue-500 text-white text-sm px-6 py-2 rounded-full" @click="simulateScan">模拟扫码成功</button>
      </view>

      <!-- Bottom -->
      <view class="h-32 w-full flex flex-col items-center justify-end pb-10 bg-gradient-to-t from-black/60 to-transparent">
         <view class="flex gap-12 text-white/80 text-sm font-medium">
            <view class="flex flex-col items-center gap-2">
                <view class="w-12 h-12 rounded-full bg-white/10 flex items-center justify-center">
                    <div class="i-material-symbols-image text-2xl"></div>
                </view>
                <text>相册</text>
            </view>
            <view class="flex flex-col items-center gap-2">
                <view class="w-12 h-12 rounded-full bg-blue-500/80 flex items-center justify-center shadow-lg shadow-blue-500/30">
                    <div class="i-material-symbols-qr-code-2 text-2xl"></div>
                </view>
                <text>我的码</text>
            </view>
            <view class="flex flex-col items-center gap-2">
                <view class="w-12 h-12 rounded-full bg-white/10 flex items-center justify-center">
                    <div class="i-material-symbols-keyboard text-2xl"></div>
                </view>
                <text>输号</text>
            </view>
         </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'

const type = ref('')

onLoad((options: any) => {
    type.value = options.type || 'dispense'
})

const goBack = () => {
    uni.navigateBack()
}

const simulateScan = () => {
    uni.showLoading({ title: '识别中...' })
    setTimeout(() => {
        uni.hideLoading()
        if (type.value === 'buy') {
            uni.redirectTo({ url: '/pages/card/buy' })
        } else {
            uni.redirectTo({ url: '/pages/scan/dispense' })
        }
    }, 800)
}
</script>
