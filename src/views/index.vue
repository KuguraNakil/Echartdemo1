<script setup>
import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入

const chart = ref();//创建dom引用

onMounted(()=>{

  var myChart = echarts.init(chart.value);
// 绘制图表
  var option = {
  title: {
    text: 'ECharts 入门示例'
  },
  tooltip: {},
  xAxis: {
    data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
  },
  yAxis: {},
  series: [
    {
      name: '销量',
      type: 'bar',
      data: [5, 20, 36, 10, 10, 20]
    }
  ]
};

  
myChart.setOption(option);

})
</script>

<template>

 <!-- 11 -->
 <!-- <div class="he">你好</div> -->
 <div>

  <div ref="chart" style="width: 1080px;height: 1000px;"></div>
 </div>

</template>

<style scoped>

</style>


<!-- <style lang="sass" scoped>

</style> -->