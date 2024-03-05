<template>
    <!-- 考勤 -->
    <div class="attendance">

        <div class="attendance-top">

            <div class="top-title">
                考勤
            </div>

            <div class="top-more">
                更多>
            </div>
        </div>

        <!-- 图表 -->
        <div class="attendance-chart">
            <div class="char" ref="chart" style="width:100%;height:267px;"></div>


        </div>

        <!-- 图表数据 -->
        <div class="chart-data">
            <div class="data" v-for="(item,index) in chardata" :key="index">
                {{item}}
            </div>


        </div>

    </div>
</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
const chart = ref();//创建dom引用
let chardata =["97%","2%","1%"]

onMounted(() => {

    var myChart = echarts.init(chart.value);
    // 绘制图表
    var option = {
        angleAxis: {
            show: false,

        },
        radiusAxis: {
            type: 'category',
            data: ['a', 'b', 'c'],
            show: false,
            z: 10
        },
        polar: {

        },
        series: [
            {
                type: 'bar',
                data: [0.2, 0, 0],
                coordinateSystem: 'polar',
                show: false,
                name: '旷工',
                barMaxWidth: 12,
                stack: 'a',
                color: "rgba(35, 39, 89, 1)",
                emphasis: {
                    focus: 'series'
                }
            },
            {
                type: 'bar',
                data: [0, 0.3, 0],
                coordinateSystem: 'polar',
                name: '请假',
                barMaxWidth: 12,
                stack: 'a',
                color: "rgba(59, 84, 211, 1)",
                emphasis: {
                    focus: 'series'
                }
            },
            {
                type: 'bar',
                data: [0, 0, 1],
                coordinateSystem: 'polar',
                barMaxWidth: 12,
                name: '实到',
                color: "rgba(241, 15, 106, 1)",
                stack: 'a',
                emphasis: {
                    focus: 'series'
                }
            }
        ],
        legend: {
            show: true,
            data: ['实到', '请假', '旷工'],
            padding: 0,
            itemGap: 40,
            itemWidth: 15,
            itemHeight: 15,
            bottom: "bottom",
            textStyle: {
                color: "rgba(255, 255, 255, 1)"
            }

        }
    };

    myChart.setOption(option);
     // 响应式
     window.addEventListener("resize",  ()=> {
        myChart.resize();
    })

})

</script>

<style lang="scss" scoped>
.attendance {
    // position: relative;
    left: 0px;
    top: -15px;
    width: 100%;
    height: 362px;
    opacity: 1;
    border: 1px solid rgba(35, 39, 89, 1);
    border-radius: 10px;
    margin-bottom: 10px;


    .attendance-top {
        display: flex;
        justify-content: space-between;
        margin: 26px;

        .top-title {
            font-size: 20px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 27.44px;
            color: rgba(255, 255, 255, 1);
            text-align: center;
            vertical-align: top;
        }

        .top-more {
            font-size: 16px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 21.95px;
            color: rgba(98, 99, 120, 1);
            text-align: center;
            vertical-align: top;

        }
    }

    .attendance-chart {
       
        margin-top: -30px;
        /* 添加此行 */


    }
    .chart-data{
        display: flex;
        justify-content: center;    
        align-items: center;

        .data{
            margin: 10px 30px 15px 30px;
            text-align: center;
            font-size: 15px;


        }
    }

}
</style>