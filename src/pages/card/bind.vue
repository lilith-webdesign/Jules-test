<template>
  <view class="bg-gray-50 min-h-screen flex flex-col">
    <!-- Main -->
    <view class="flex-1 px-5 py-8 flex flex-col">
       <view class="flex flex-col items-center mb-10">
          <view class="w-24 h-24 bg-blue-50 rounded-full flex items-center justify-center mb-6">
             <div class="i-material-symbols-credit-card text-blue-500 text-5xl"></div>
          </view>
          <text class="text-2xl font-bold text-gray-900 mb-2 text-center">绑定您的水卡</text>
          <text class="text-gray-500 text-center leading-relaxed">请输入社区智能饮水机配套水卡\n背面的8-12位卡号进行绑定</text>
       </view>

       <view class="space-y-6">
          <view class="flex flex-col gap-2">
             <label class="text-sm font-medium text-gray-700 ml-1">水卡卡号</label>
             <view class="relative group">
                <view class="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400">
                   <div class="i-material-symbols-pin text-xl"></div>
                </view>
                <input class="w-full pl-12 pr-4 h-14 bg-white border border-gray-200 rounded-xl text-gray-900 text-lg tracking-wider" placeholder="请输入水卡卡号" />
             </view>
          </view>
          <view class="pt-4">
             <button class="w-full h-14 bg-blue-500 hover:bg-blue-600 active:scale-[0.98] text-white text-lg font-bold rounded-xl shadow-lg shadow-blue-500/20 flex items-center justify-center gap-2 border-none" @click="bindCard">
               <text>立即绑定</text>
               <div class="i-material-symbols-arrow-forward"></div>
             </button>
          </view>
       </view>

       <view class="mt-auto py-8">
          <view class="p-4 bg-gray-100 rounded-xl border border-gray-200">
             <view class="flex gap-3">
               <div class="i-material-symbols-info text-gray-400 text-xl"></div>
               <view class="flex-1">
                  <text class="text-sm font-semibold text-gray-700 mb-1 block">温馨提示</text>
                  <text class="text-xs text-gray-500 leading-relaxed block">
                    1. 绑定后可实时查看余额与消费记录。\n
                    2. 每个手机号最多可绑定3张水卡。\n
                    3. 如遇卡号模糊，请联系社区物业处理。
                  </text>
               </view>
             </view>
          </view>
       </view>
    </view>
  </view>
</template>

<script setup lang="ts">
const bindCard = () => {
    uni.showToast({ title: '绑定成功', icon: 'success' })
    setTimeout(() => {
        uni.navigateBack()
    }, 1500)
}
</script>
