<template>
  <div class="room-use">
    <div ref="chart" style="width:100%;height: 500px;"></div>
  </div>
</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
const chart = ref();//创建dom引用

onMounted(() => {
  var myChart = echarts.init(chart.value);
  // 绘制图表
  var option = {
    title: {
      text: '会议室使用情况',
      top: "15",
      left: "15",
      bottom:"40",
      textStyle: {
        fontSize: 18,
        color: "white",
        fontWeight: "500"
      },

    },
    xAxis: {
    data: ['星期一','星期二', '星期三', '星期四', '星期五']
  },
  yAxis: {
      type: 'value',
    min:1651363200,
    max:1651413600,
    splitNumber:8,
    
    axisLabel:{
      formatter:function(e){
        return timestampToTime(e);
      },
   
    }

  },
  series: [
    {
      type: 'candlestick',
      data: [
        [1651372200, 1651393400, 1651372200, 1651393400],
        [1651371200, 1651373400, 1651371200, 1651373400],
        [1651372200, 1651378400, 1651372200, 1651378400],
         [1651375200, 1651383400, 1651375200, 1651383400],
           [1651395200, 1651409400, 1651395200, 1651409400],
      ],
      itemStyle:{
      color: "rgba(59, 84, 211, 1)"
    },
    },
   
  ]
  };
  // data: [[new Date('2023-12-04T8:00:00').getTime(), new Date('2023-12-04T10:00:00').getTime()], [new Date('2023-12-04T10:00:00').getTime(), new Date('2023-12-04T16:00:00').getTime()], [new Date('2023-12-04T16:00:00').getTime(), new Date('2023-12-04T18:00:00').getTime()]] // 柱状图的瀑布模型数据
  function timestampToTime(timestamp) {
        var date = new Date(timestamp * 1000);//时间戳为10位需*1000，时间戳为13位的话不需乘1000
        var Y = date.getFullYear() + '-';
        var M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-';
        var D = (date.getDate() < 10 ? '0'+ date.getDate() : date.getDate()) + ' ';
        var h = (date.getHours() < 10 ? '0'+ date.getHours() : date.getHours()) + ':';
        var m = (date.getMinutes() < 10 ? '0'+ date.getMinutes() : date.getMinutes()) + ':';
        var s = (date.getSeconds() < 10 ? '0'+ date.getSeconds() : date.getSeconds());
        return h+m;
    }

  myChart.setOption(option);
  // 响应式
  window.addEventListener("resize", () => {
    myChart.resize();
  })

})

</script>

<style lang="scss" scoped>
.room-use {
  display: flex;
  justify-content: center;
  align-items: center;
  
  width: 100%;
  height: 578px;
  opacity: 1;
  border: 1px solid rgba(35, 39, 89, 1);
  border-radius: 10px;
  margin: 0 auto;

}
</style>