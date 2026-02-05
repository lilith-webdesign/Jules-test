<template>
  <view class="bg-gray-50 min-h-screen pb-24">
    <!-- Header Device Info -->
    <view class="px-4 py-4">
      <view class="flex items-center gap-4 bg-white p-4 rounded-xl shadow-sm border border-gray-200">
        <view class="flex items-center justify-center rounded-lg bg-blue-50 shrink-0 w-12 h-12 text-blue-500">
          <div class="i-material-symbols-qr-code-scanner text-2xl"></div>
        </view>
        <view class="flex flex-col flex-1 min-w-0">
          <text class="text-gray-900 text-base font-semibold truncate">设备编号: 89304821</text>
          <text class="text-gray-500 text-sm font-normal truncate">所属社区: 阳光花园小区</text>
        </view>
        <button class="shrink-0 text-blue-500 text-sm font-medium px-3 py-1.5 rounded-lg bg-transparent border-none">详情</button>
      </view>
    </view>

    <!-- Form -->
    <view class="flex flex-col gap-5 px-4">
      <view class="flex flex-col w-full">
        <text class="text-gray-900 text-sm font-medium pb-2">收货人姓名</text>
        <view class="relative">
          <input class="w-full rounded-lg border border-gray-300 bg-white h-12 px-4 text-base pl-4 pr-10" placeholder="请输入姓名" />
          <view class="absolute right-3 top-3 text-gray-400 pointer-events-none">
             <div class="i-material-symbols-person text-xl"></div>
          </view>
        </view>
      </view>

      <view class="flex flex-col w-full">
        <text class="text-gray-900 text-sm font-medium pb-2">联系电话</text>
        <view class="relative">
          <input class="w-full rounded-lg border border-gray-300 bg-white h-12 px-4 text-base pl-4 pr-10" placeholder="请输入手机号码" type="tel" />
          <view class="absolute right-3 top-3 text-gray-400 pointer-events-none">
             <div class="i-material-symbols-call text-xl"></div>
          </view>
        </view>
      </view>

      <view class="flex flex-col w-full">
        <text class="text-gray-900 text-sm font-medium pb-2">户号/门牌号</text>
        <view class="relative">
          <input class="w-full rounded-lg border border-gray-300 bg-white h-12 px-4 text-base pl-4 pr-10" placeholder="例如：3栋2单元501" />
          <view class="absolute right-3 top-3 text-gray-400 pointer-events-none">
             <div class="i-material-symbols-home text-xl"></div>
          </view>
        </view>
      </view>

      <view class="flex flex-col w-full">
        <text class="text-gray-900 text-sm font-medium pb-2">详细邮寄地址</text>
        <textarea class="w-full rounded-lg border border-gray-300 bg-white p-4 h-[100px] text-base" placeholder="请输入街道、小区详细地址等信息"></textarea>
      </view>

      <!-- Warning -->
      <view class="flex gap-3 bg-orange-50 border border-orange-100 p-4 rounded-lg mt-2">
         <div class="i-material-symbols-info text-orange-500 text-xl mt-0.5"></div>
         <text class="text-orange-800 text-sm leading-relaxed">
           <text class="font-medium">温馨提示：</text>受物流影响，实体卡配送可能存在3-5天延迟，请耐心等待。
         </text>
      </view>
    </view>

    <!-- Bottom Bar -->
    <view class="fixed bottom-0 left-0 right-0 bg-white p-4 border-t border-gray-200 safe-area-pb">
      <view class="max-w-[640px] mx-auto">
        <view class="flex items-center justify-between mb-2 px-1">
          <text class="text-sm text-gray-500">实付金额:</text>
          <text class="text-xl font-bold text-gray-900">¥20.00</text>
        </view>
        <button class="w-full h-12 bg-blue-500 hover:bg-blue-600 text-white rounded-xl text-base font-semibold shadow-lg shadow-blue-500/25 flex items-center justify-center gap-2 border-none" @click="submitOrder">
           <div class="i-material-symbols-payments text-xl"></div>
           <text>支付并购卡</text>
        </button>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
const submitOrder = () => {
    uni.showToast({ title: '订单提交成功', icon: 'success' })
    setTimeout(() => {
        uni.navigateBack()
    }, 1500)
}
</script>
