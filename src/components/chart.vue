<template>
    <!-- 饼图1 -->
    <div class="bindchart">


        <!-- 图表 -->
        <div class="bindchart-chart">
            <div class="char" ref="chart" style="width:100%;height:250px;"></div>

        </div>

        <!-- 图表数据 -->
        <div class="Bindchart-data">
            <div class="data" v-for="(item, index) in chardata" :key="index">
                {{ item }}
            </div>


        </div>

    </div>
</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
const chart = ref();//创建dom引用
let chardata = ["10%", "90%"]

onMounted(() => {

    var myChart = echarts.init(chart.value);
    // 绘制图表
    var option = {
        title: {

            text: '流程使用率',
            top: "15",
            left:"31.5",
            textStyle: {
                fontSize: 20,
                color: "rgba(205, 214, 229, 1)",
                fontWeight: "500"
            },

        },
        tooltip: {
            trigger: 'item'
        },
        legend: {
            padding: 0,
            itemGap: 40,
            itemWidth: 15,
            itemHeight: 15,
            bottom: "bottom",
            textStyle: {
                color: "rgba(255, 255, 255, 1)"
            }

        },
        series: [
            {
                top: "15%",
                name: 'Access From',
                type: 'pie',
                startAngle: 50,
                radius: ['40%', '70%'],
                avoidLabelOverlap: false,
                label: {
                    show: false,
                    position: 'center'
                },
                emphasis: {
                    label: {
                        show: true,
                        fontSize: 40,
                        fontWeight: 'bold'
                    }
                },
                labelLine: {
                    show: false
                },
                data: [
                    {
                        value: 10,
                        name: '请假',
                        itemStyle: {
                            color: "rgba(241, 15, 106, 1)"
                        }
                    },
                    {
                        value: 90,
                        name: '报销',
                        itemStyle: {
                            color: "rgba(59, 84, 211, 1)"
                        }
                    },

                ]
            }
        ]
    };

    myChart.setOption(option);
     // 响应式
     window.addEventListener("resize",  ()=> {
        myChart.resize();
    })

})

</script>

<style lang="scss" scoped>
.bindchart {
    // position: relative;
    left: 0px;
    top: -15px;
    width: 100%;
    height: 305px;
    opacity: 1;
    border: 1px solid rgba(35, 39, 89, 1);
    border-radius: 10px;
    margin-bottom: 10px;


    

    .bindchart-chart {

        margin-top: 10px;
        /* 添加此行 */


    }

   

    .Bindchart-data{
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