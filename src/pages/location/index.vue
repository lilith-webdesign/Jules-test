<template>
  <view class="bg-gray-50 min-h-screen flex flex-col h-screen overflow-hidden">
    <!-- Header Search -->
    <view class="bg-white shadow-sm z-10 shrink-0">
       <view class="px-4 py-3">
         <view class="flex w-full items-center rounded-xl h-12 bg-gray-100 px-4">
           <div class="i-material-symbols-search text-gray-500 text-xl mr-2"></div>
           <input class="flex-1 bg-transparent text-gray-900 h-full text-base" placeholder="输入详细地址查询周边饮水点" />
         </view>
       </view>
       <!-- Chips -->
       <view class="flex gap-3 px-4 pb-4 overflow-x-auto">
         <view class="flex h-8 items-center justify-center px-4 rounded-full bg-blue-500 text-white shadow-sm">
           <text class="text-sm font-medium">全部</text>
         </view>
         <view class="flex h-8 items-center justify-center px-4 rounded-full bg-white border border-gray-200">
           <text class="text-gray-700 text-sm font-medium">距离最近</text>
         </view>
         <view class="flex h-8 items-center justify-center px-4 rounded-full bg-white border border-gray-200">
           <text class="text-gray-700 text-sm font-medium">仅看在线</text>
         </view>
       </view>
    </view>

    <!-- List -->
    <scroll-view scroll-y class="flex-1 p-4 box-border h-0">
      <view class="space-y-4 pb-10">
        <!-- Item 1 -->
        <view class="bg-white rounded-xl p-4 shadow-sm border border-gray-100 flex flex-col gap-3 active:scale-99 transition-transform" @click="goDetail">
          <view class="flex justify-between items-start">
            <view class="flex items-start gap-4 flex-1">
              <view class="text-blue-500 flex items-center justify-center rounded-xl bg-blue-50 shrink-0 w-12 h-12">
                 <div class="i-material-symbols-water-drop text-3xl"></div>
              </view>
              <view class="flex flex-col">
                <view class="flex items-center gap-2">
                  <text class="text-gray-900 text-base font-bold">设备编号 NO.001</text>
                  <text class="bg-green-50 text-green-700 px-2 py-0.5 text-xs rounded-full font-medium">在线</text>
                </view>
                <text class="text-gray-500 text-sm mt-1 leading-relaxed">阳光小区3号楼东侧花园旁</text>
              </view>
            </view>
            <view class="flex flex-col items-end shrink-0 pl-2">
              <text class="text-blue-500 font-semibold text-sm">200m</text>
              <div class="i-material-symbols-chevron-right text-gray-300 text-xl mt-2"></div>
            </view>
          </view>
          <view class="h-px bg-gray-100 w-full"></view>
          <view class="flex justify-between items-center text-xs text-gray-400">
             <view class="flex items-center gap-1">
               <div class="i-material-symbols-schedule"></div>
               <text>营业时间: 24小时</text>
             </view>
             <view class="flex items-center gap-1">
               <div class="i-material-symbols-local-drink"></div>
               <text>水温: 45°C - 98°C</text>
             </view>
          </view>
        </view>

        <!-- Item 2 -->
        <view class="bg-white rounded-xl p-4 shadow-sm border border-gray-100 flex flex-col gap-3 active:scale-99 transition-transform">
          <view class="flex justify-between items-start">
            <view class="flex items-start gap-4 flex-1">
              <view class="text-blue-500 flex items-center justify-center rounded-xl bg-blue-50 shrink-0 w-12 h-12">
                 <div class="i-material-symbols-water-drop text-3xl"></div>
              </view>
              <view class="flex flex-col">
                <view class="flex items-center gap-2">
                  <text class="text-gray-900 text-base font-bold">设备编号 NO.005</text>
                  <text class="bg-green-50 text-green-700 px-2 py-0.5 text-xs rounded-full font-medium">在线</text>
                </view>
                <text class="text-gray-500 text-sm mt-1 leading-relaxed">阳光小区南门健身区</text>
              </view>
            </view>
            <view class="flex flex-col items-end shrink-0 pl-2">
              <text class="text-blue-500 font-semibold text-sm">350m</text>
              <div class="i-material-symbols-chevron-right text-gray-300 text-xl mt-2"></div>
            </view>
          </view>
          <view class="h-px bg-gray-100 w-full"></view>
          <view class="flex justify-between items-center text-xs text-gray-400">
             <view class="flex items-center gap-1">
               <div class="i-material-symbols-schedule"></div>
               <text>营业时间: 06:00 - 23:00</text>
             </view>
          </view>
        </view>

        <view class="flex items-center justify-center py-4">
          <text class="text-gray-400 text-xs">没有更多设备了</text>
        </view>
      </view>
    </scroll-view>
  </view>
</template>

<script setup lang="ts">
const goDetail = () => {
    uni.navigateTo({ url: '/pages/scan/dispense' })
}
</script>
