<template>
  <view class="bg-gray-50 min-h-screen flex flex-col pb-10">
    <!-- Header -->
    <view class="px-4 py-2 mt-4 z-10">
      <text class="text-2xl font-bold text-gray-900 px-2">卡片</text>
    </view>

    <!-- Stack -->
    <view class="flex flex-col items-center w-full max-w-md mx-auto relative pt-2 px-4">
      <!-- Card 1 -->
      <view class="relative w-full aspect-[1.586/1] rounded-2xl shadow-lg transition-transform duration-300 hover:-translate-y-2 z-30 mb-[-100px]">
         <view class="absolute inset-0 bg-gradient-to-br from-blue-500 to-blue-700 rounded-2xl p-6 flex flex-col justify-between overflow-hidden">
            <view class="absolute -right-12 -top-12 w-48 h-48 bg-white/10 rounded-full blur-2xl"></view>
            <view class="flex justify-between items-start z-10">
               <view class="flex items-center gap-3">
                  <view class="w-10 h-10 rounded-full bg-white/20 flex items-center justify-center backdrop-blur-sm border border-white/10">
                     <div class="i-material-symbols-water-drop text-white"></div>
                  </view>
                  <text class="font-medium text-lg text-white tracking-wide">电子水卡</text>
               </view>
               <div class="i-material-symbols-contactless text-white/60"></div>
            </view>
            <view class="flex flex-col gap-1 z-10">
               <text class="text-white/70 text-sm font-mono tracking-wider">**** 8842</text>
               <view class="flex items-baseline gap-1">
                  <text class="text-2xl text-white font-bold">¥</text>
                  <text class="text-4xl text-white font-bold tracking-tighter">56.00</text>
               </view>
            </view>
         </view>
      </view>

      <!-- Card 2 -->
      <view class="relative w-full aspect-[1.586/1] rounded-2xl shadow-lg transition-transform duration-300 hover:-translate-y-4 z-20 top-[60px]">
         <view class="absolute inset-0 bg-gradient-to-br from-indigo-500 to-purple-700 rounded-2xl p-6 flex flex-col justify-between overflow-hidden border-t border-white/10">
            <view class="flex justify-between items-start z-10">
               <view class="flex items-center gap-3">
                  <view class="w-10 h-10 rounded-full bg-white/20 flex items-center justify-center backdrop-blur-sm border border-white/10">
                     <div class="i-material-symbols-credit-card text-white"></div>
                  </view>
                  <text class="font-medium text-lg text-white tracking-wide">实体水卡</text>
               </view>
               <div class="i-material-symbols-wifi text-white/60"></div>
            </view>
            <view class="flex flex-col gap-1 z-10">
               <text class="text-white/70 text-sm font-mono tracking-wider">**** 1029</text>
               <view class="flex items-baseline gap-1">
                  <text class="text-2xl text-white font-bold">¥</text>
                  <text class="text-4xl text-white font-bold tracking-tighter">12.50</text>
               </view>
            </view>
         </view>
      </view>

      <!-- Spacer for stack effect visualization -->
      <view class="h-24 w-full"></view>
    </view>

    <!-- History -->
    <view class="mt-8 px-6 z-10">
       <text class="text-lg font-bold text-gray-900 mb-4 block">最近活动</text>
       <view class="bg-white rounded-xl p-4 shadow-sm space-y-4">
          <view class="flex items-center justify-between">
             <view class="flex items-center gap-3">
                <view class="w-10 h-10 rounded-full bg-blue-100 flex items-center justify-center text-blue-500">
                   <div class="i-material-symbols-water-drop text-xl"></div>
                </view>
                <view class="flex flex-col">
                   <text class="text-sm font-medium text-gray-900">饮水机消费</text>
                   <text class="text-xs text-gray-500">电子水卡 (8842)</text>
                </view>
             </view>
             <view class="text-right">
                <text class="block text-sm font-bold text-gray-900">- ¥2.50</text>
                <text class="block text-xs text-gray-500">今天 14:30</text>
             </view>
          </view>
          <view class="h-px w-full bg-gray-100"></view>
          <view class="flex items-center justify-between">
             <view class="flex items-center gap-3">
                <view class="w-10 h-10 rounded-full bg-green-100 flex items-center justify-center text-green-600">
                   <div class="i-material-symbols-account-balance-wallet text-xl"></div>
                </view>
                <view class="flex flex-col">
                   <text class="text-sm font-medium text-gray-900">充值成功</text>
                   <text class="text-xs text-gray-500">微信支付</text>
                </view>
             </view>
             <view class="text-right">
                <text class="block text-sm font-bold text-green-600">+ ¥50.00</text>
                <text class="block text-xs text-gray-500">昨天 09:12</text>
             </view>
          </view>
       </view>
    </view>
  </view>
</template>

<script setup lang="ts">
// Logic here
</script>
