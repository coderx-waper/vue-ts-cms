<template>
  <div class="layer">
    <base-echart :options="options"></base-echart>
  </div>
</template>
<script setup lang="ts">
import { computed, defineProps } from 'vue'
import BaseEchart from '@/base-ui/echarts'
import { IEchartDataItem } from '@/components/page-echarts/types'

// 定义属性
// 需要外界传
const props = defineProps<{
  data: IEchartDataItem[]
}>()

const options = computed(() => {
  return {
    // legend: {
    //   top: 'bottom'
    // },
    toolbox: {
      show: true,
      feature: {
        mark: { show: true },
        dataView: { show: true, readOnly: false },
        restore: { show: true },
        saveAsImage: { show: true }
      }
    },
    series: [
      {
        name: '类别数据',
        type: 'pie',
        radius: [10, 100],
        center: ['50%', '50%'],
        roseType: 'area',
        itemStyle: {
          borderRadius: 8
        },
        data: props.data
      }
    ]
  }
})
</script>
<style scoped lang="less"></style>
