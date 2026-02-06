<template>
  <view class="bg-gray-50 min-h-screen flex flex-col h-screen overflow-hidden">
    <!-- Header Search & Filter -->
    <view class="bg-white pt-2 pb-4 shadow-sm z-40 shrink-0">
        <view class="px-4 mb-4">
            <view class="relative group">
                <view class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <div class="i-material-symbols-search text-gray-400"></div>
                </view>
                <input class="block w-full pl-10 pr-3 py-3 rounded-xl bg-gray-100 text-gray-900 placeholder-gray-400 text-sm border-none" placeholder="搜索记录 (如: 充值、金额)" />
            </view>
        </view>

        <scroll-view scroll-x class="whitespace-nowrap px-4" :show-scrollbar="false">
            <view class="flex gap-3 pb-1">
                <view
                  v-for="tab in tabs"
                  :key="tab.value"
                  class="inline-flex px-5 py-2 rounded-full text-sm font-medium transition-all"
                  :class="activeTab === tab.value ? 'bg-blue-500 text-white shadow-md' : 'bg-white text-gray-600 border border-gray-200'"
                  @click="activeTab = tab.value"
                >
                    <text>{{ tab.label }}</text>
                </view>
            </view>
        </scroll-view>
    </view>

    <!-- Content -->
    <scroll-view scroll-y class="flex-1 px-4 pb-8 box-border h-0 bg-gray-50">
        <view class="pt-4 space-y-6">
            <!-- This Month -->
            <view>
                <view class="flex items-center justify-between mb-3 px-1">
                    <text class="text-sm font-bold text-gray-500">本月</text>
                    <text class="text-xs text-gray-400 bg-gray-100 px-2 py-1 rounded">支出 ¥124.50</text>
                </view>

                <view class="flex flex-col gap-3">
                    <view class="bg-white rounded-2xl p-4 shadow-sm flex items-start gap-3">
                        <view class="flex items-center justify-center w-12 h-12 rounded-full bg-blue-50 text-blue-500 shrink-0">
                            <div class="i-material-symbols-water-drop"></div>
                        </view>
                        <view class="flex-1 min-w-0 pt-0.5">
                            <view class="flex justify-between items-center mb-1">
                                <text class="text-base font-bold text-gray-900 truncate">社区3号机 - 直饮水</text>
                                <text class="text-base font-bold text-gray-900">-¥1.50</text>
                            </view>
                            <view class="flex justify-between items-center">
                                <text class="text-sm text-gray-500">今天 14:30</text>
                                <text class="text-xs text-gray-400">余额 ¥148.50</text>
                            </view>
                            <view class="mt-2 flex items-center gap-2">
                                <view class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-gray-100 text-gray-600">
                                    <div class="i-material-symbols-opacity text-xs mr-1"></div>
                                    <text>出水量: 3.0L</text>
                                </view>
                            </view>
                        </view>
                    </view>

                    <view class="bg-white rounded-2xl p-4 shadow-sm flex items-start gap-3">
                        <view class="flex items-center justify-center w-12 h-12 rounded-full bg-green-50 text-green-600 shrink-0">
                            <div class="i-material-symbols-account-balance-wallet"></div>
                        </view>
                        <view class="flex-1 min-w-0 pt-0.5">
                            <view class="flex justify-between items-center mb-1">
                                <text class="text-base font-bold text-gray-900">微信充值</text>
                                <text class="text-base font-bold text-blue-500">+¥50.00</text>
                            </view>
                            <view class="flex justify-between items-center">
                                <text class="text-sm text-gray-500">10月27日 09:15</text>
                                <text class="text-xs text-gray-400">余额 ¥150.00</text>
                            </view>
                            <view class="mt-2 flex items-center gap-2">
                                <view class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-green-50 text-green-700 border border-green-100">
                                    <text>普通会员卡</text>
                                </view>
                            </view>
                        </view>
                    </view>
                </view>
            </view>

             <!-- Last Month -->
            <view class="mt-6">
                <view class="flex items-center justify-between mb-3 px-1">
                    <text class="text-sm font-bold text-gray-500">上月</text>
                    <text class="text-xs text-gray-400 bg-gray-100 px-2 py-1 rounded">支出 ¥40.00</text>
                </view>
                <view class="flex flex-col gap-3">
                    <view class="bg-white rounded-2xl p-4 shadow-sm flex items-start gap-3">
                        <view class="flex items-center justify-center w-12 h-12 rounded-full bg-purple-50 text-purple-500 shrink-0">
                            <div class="i-material-symbols-badge"></div>
                        </view>
                        <view class="flex-1 min-w-0 pt-0.5">
                            <view class="flex justify-between items-center mb-1">
                                <text class="text-base font-bold text-gray-900">新卡购买</text>
                                <text class="text-base font-bold text-gray-900">-¥20.00</text>
                            </view>
                            <view class="flex justify-between items-center">
                                <text class="text-sm text-gray-500">9月15日 10:00</text>
                                <text class="inline-flex items-center px-2 py-0.5 rounded-full text-xs font-medium bg-gray-100 text-gray-500">已完成</text>
                            </view>
                            <view class="mt-3 p-3 bg-gray-50 rounded-lg border border-gray-100">
                                <view class="flex gap-2">
                                    <div class="i-material-symbols-local-shipping text-gray-400 text-sm mt-0.5 shrink-0"></div>
                                    <view>
                                        <text class="text-xs font-semibold text-gray-700 mb-0.5 block">邮寄地址</text>
                                        <text class="text-xs text-gray-500 leading-relaxed block">北京市朝阳区阳光100社区3号楼2单元501室</text>
                                    </view>
                                </view>
                            </view>
                        </view>
                    </view>
                </view>
            </view>

            <view class="py-4 text-center">
                <text class="text-xs text-gray-400">没有更多记录了</text>
            </view>
        </view>
    </scroll-view>
  </view>
</template>

<script setup lang="ts">
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'

const activeTab = ref('all')

const tabs = [
    { label: '全部', value: 'all' },
    { label: '充值记录', value: 'recharge' },
    { label: '打水记录', value: 'dispense' },
    { label: '购卡记录', value: 'buy' },
]

onLoad((options: any) => {
    console.log('Record Page onLoad options:', options)
    console.log('Current URL:', window.location.href)
    if (options && options.type) {
        activeTab.value = options.type
    } else {
        // Fallback for H5 if options are missing
        const urlParams = new URLSearchParams(window.location.hash.split('?')[1]);
        const type = urlParams.get('type');
        if (type) {
            console.log('Fallback type from URL:', type);
            activeTab.value = type;
        }
    }
})
</script>
