<template>
    <!-- 考勤 -->
    <div class="notice">
        <div class="notice-left">
            <div class="title">
                待审核
            </div>



        </div>
        <!-- 中间内容部分 -->
        <div class="notice-mid">
            <!-- 特殊边框 -->
            <div class="notice-border"></div>
            <div class="notice-bordertwo"></div>
            <div class="mid-content">
                <div class="mid-content-top">
                    <!-- //头部 -->
                    <div class="head" v-for="(item, index) in contenthead" :key="index">
                        <span>{{ item }}</span>
                    </div>

                </div>

                <div class="mid-content-bottom" v-for="(item, index) in content" :key="index">

                    <div class="mid-content-data">
                        {{ item.num }}

                    </div>
                    <div class="mid-content-data">
                        {{ item.name }}

                    </div>
                    <div class="mid-content-data">
                        {{ item.time }}

                    </div>
                    <div class="mid-content-data">
                        {{ item.architect }}

                    </div>
                </div>



            </div>
        </div>
        <!-- 右边 -->


        <div class="notiec-right">
            <!-- 特殊边框 -->
            <div class="notice-border"></div>
            <div class="notice-bordertwo"></div>

            <div class="char" ref="chart" style="width:100%;height:170px;"></div>
            <div class="right-data">
                <div class="data" v-for="(item, index) in value" :key="index">
                    {{ item }}个事项
                </div>


            </div>
        </div>

        <!-- 图表 -->

        <!-- 图表数据 -->



    </div>
</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
const chart = ref();//创建dom引用

let contenthead = ["审核编号", "作品名称", "上传时间", "设计师"]

let content = [
    {
        "num": "0001",
        "name": "惊蛰启动页",
        "time": "2019-2-19",
        "architect": "陈一",
    },
    {
        "num": "0002",
        "name": "女神节专题网页",
        "time": "2019-2-19",
        "architect": "吴十",
    },
    {
        "num": "0003",
        "name": "科技风H5",
        "time": "2019-2-19",
        "architect": "严数",
    }
]

let value = ["100"]







onMounted(() => {

    var myChart = echarts.init(chart.value);

    // 绘制图表
    var option = {

        title: {

            text: '完成度',
            top: "15",
            left: "15",
            textStyle: {
                fontSize: 18,
                color: "rgba(205, 214, 229, 1)",
                fontWeight: "500"
            },

        },
        series: [
            {
                bottom: "bottom",
                name: 'hour',
                left: "15",
                type: 'gauge',
                startAngle: 90,
                endAngle: -270,
                min: 0,
                max: 100,
                splitNumber: 5,
                clockwise: true,
                axisLine: {

                    lineStyle: {

                        width: 3,
                        color: [[5, 'white']],
                        shadowColor: 'rgba(0, 0, 0, 0.5)',

                    }
                },
                axisTick: {
                    show: false
                },
                axisLabel: {
                    show: false
                },
                splitLine: {
                    show: true,
                    lineStyle: {
                        color: "rgba(0, 186, 255, 1)"
                    }

                },

                detail: {
                    show: true,
                    formatter: "{value}%",
                    color: "rgba(255, 255, 255, 1)",
                    fontSize: 15

                },
                title: {
                    offsetCenter: [0, '30%']
                },
                data: [
                    {
                        value: 85
                    }
                ]
            },
        ]



    };

    myChart.setOption(option);
    // 响应式
    window.addEventListener("resize", () => {
        myChart.resize();
    })




})

</script>

<style lang="scss" scoped>
.notice {
    width: 100%;
    height: 230px;
    border: 1px solid rgba(35, 39, 89, 1);
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    margin-top: 30px;

    





    .notice-left {

        width: 12%;

        .title {
            font-size: 20px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 27.44px;
            color: rgba(255, 255, 255, 1);
            padding: 20px;
            vertical-align: top;

            /* 设置为1行 */
        }


    }

    .notice-mid {
        width: 58%;
        // border: 1px solid rgba(35, 39, 89, 1);0
        position: relative;

        .notice-border {
        position: absolute;
        width: 20px;
        height: 20px;
        top: 0;
        right: 0;
        border-top: 3px solid #3B54D3;
        border-right: 2px solid #3B54D3;
        z-index: 5;
    }
    .notice-bordertwo{
        position: absolute;
        width: 20px;
        height: 20px;
        bottom: 0;
        right: 0;
        border-bottom: 3px solid #3B54D3;
        border-right: 2px solid #3B54D3;
        z-index: 5;
    }

        .mid-content {
            border-right: 1px solid rgba(35, 39, 89, 1);

            .mid-content-top {
                display: flex;
                justify-content: space-between;
                align-items: center;
                flex-wrap: wrap;
                margin-top: 35px;
                margin-left: 40px;
               


                .head {
                    font-size: 18px;
                    font-weight: 500;
                    letter-spacing: 0px;
                    line-height: 24.7px;
                    color: rgba(59, 84, 211, 1);
                    width: 20%;
                    display: -webkit-box;
                    -webkit-box-orient: vertical;
                    overflow: hidden;
                    -webkit-line-clamp: 1;
                }
            }

            .mid-content-bottom {
                display: flex;
                justify-content: space-between;
                align-items: center;
                flex-wrap: wrap;
                margin-top: 20px;
                margin-left: 20px;


                text-align: center;


                .mid-content-data {
                    width: 25%;
                    font-size: 16px;
                    font-weight: 500;
                    letter-spacing: 0px;
                    line-height: 24.7px;
                    color: rgba(127, 144, 171, 1);
                    text-align: center;
                    vertical-align: top;
                    display: -webkit-box;
                    -webkit-box-orient: vertical;
                    overflow: hidden;
                    -webkit-line-clamp: 1;
                    /* 设置为1行 */



                }


            }

        }


    }

    .notiec-right {
        position: relative;
        width: 30%;
       
        .notice-border {
        position: absolute;
        width: 20px;
        height: 20px;
        top: 0;
        left: 0;
        border-top: 3px solid #3B54D3;
        border-left: 2px solid #3B54D3;
        z-index: 5;
    }
    .notice-bordertwo{
        position: absolute;
        width: 20px;
        height: 20px;
        bottom: 0;
        left: 0;
        border-bottom: 3px solid #3B54D3;
        border-left: 2px solid #3B54D3;
        z-index: 5;
    }

        // .char {}

        .right-data {
            display: flex;
            justify-content: center;
            align-items: center;



            .data {

                font-size: 16px;
                font-weight: 500;
                letter-spacing: 0px;
                line-height: 21.95px;
                color: rgba(98, 99, 120, 1);
                text-align: center;
                vertical-align: top;
                display: -webkit-box;
                -webkit-box-orient: vertical;
                overflow: hidden;
                -webkit-line-clamp: 1;


            }
        }
    }


}
</style>