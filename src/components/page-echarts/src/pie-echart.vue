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
    tooltip: {
      trigger: 'item'
    },
    legend: {
      orient: 'horizontal',
      left: 'left'
    },
    series: [
      {
        name: '分类数据',
        type: 'pie',
        radius: '50%',
        data: props.data,
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }
    ]
  }
})
</script>
<style scoped lang="less"></style>
